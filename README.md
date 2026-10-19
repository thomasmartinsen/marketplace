# Thomas Martinsen's plugin marketplace

Independently installable GitHub Copilot CLI agents and Codex skills for content
creation, research, conference planning, strategy, capacity, relationships, and wellbeing.

## Install in Copilot CLI

```sh
copilot plugin marketplace add thomasmartinsen/marketplace
copilot plugin marketplace browse thomasmartinsen
copilot plugin install linkedin-writer@thomasmartinsen
copilot plugin install tpd-partner@thomasmartinsen
```

Start a new Copilot CLI session and select the installed agent with `/agent`.
Install any of the plugins below using `<plugin-id>@thomasmartinsen`.
Both this marketplace and the source repository are private; you need GitHub
access to both. Registration does not install any agents automatically.

## Install in Codex

```sh
codex plugin marketplace add thomasmartinsen/marketplace
codex plugin list --marketplace thomasmartinsen --available --json
codex plugin add linkedin-writer@thomasmartinsen
codex plugin add tpd-partner@thomasmartinsen
```

Start a new Codex session and ask it to use the installed plugin's skill.
The same plugin IDs below work in either client. Codex exposes these roles as
skills, not native custom subagents. Each skill includes the source profile's
instructions and the same written tool boundaries as its standalone Codex
agent profile; Codex does not enforce Copilot's per-tool allowlists.

If adding the marketplace previously failed with "marketplace root does not
contain a supported manifest", retry `codex plugin marketplace add
thomasmartinsen/marketplace`. The repository now includes Codex's
`.agents/plugins/marketplace.json` in addition to Copilot's catalog.

| Plugin ID | Purpose |
| --- | --- |
| `ai-daily-post` | Verified internal AI news with a separate personal perspective |
| `chief-of-staff` | Capacity, commitments, priorities, and protected time |
| `content-repurposer` | Faithful channel-specific content from existing material |
| `health-guardian` | Non-clinical workload, recovery, and wellbeing guidance |
| `innovation-scout` | Emerging signals, future scenarios, and bounded experiments |
| `linkedin-writer` | Practical LinkedIn posts in Thomas's personal voice |
| `opportunity-filter` | Opportunities assessed against value, cost, and commitments |
| `relationship-manager` | Thoughtful follow-ups and consent-aware introductions |
| `strategic-advisor` | Strategic options, assumption testing, and long-term decisions |
| `technical-article-writer` | Source-backed developer tutorials and explainers |
| `topic-researcher` | Timely content ideas and editorial briefs |
| `tpd-partner` | Tech Passion Day strategy, speakers, communications, social media, hosting, and operations |
| `video-scriptwriter` | Recordable video scripts and demo walkthroughs |

## Update or uninstall

```sh
copilot plugin marketplace update thomasmartinsen
copilot plugin update linkedin-writer
copilot plugin uninstall linkedin-writer
```

Repeat the update command for each installed plugin you want to refresh, or
use `copilot plugin update --all` to update all installed plugins, including
those from other marketplaces.

For Codex, refresh the catalog with `codex plugin marketplace upgrade
thomasmartinsen`, then use `codex plugin add <plugin-id>@thomasmartinsen` to
install or refresh a plugin. Remove a Codex plugin with
`codex plugin remove <plugin-id>@thomasmartinsen`.

## Sources and maintenance

Copilot reads [`.github/plugin/marketplace.json`](.github/plugin/marketplace.json);
Codex reads [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json).
The catalogs use each client's supported Git source format.
Each entry references `plugins/<plugin-id>` on `main` in
[`thomasmartinsen/agents`](https://github.com/thomasmartinsen/agents).
Agent instructions are not duplicated in this marketplace.

The agents repository retains its original Copilot and Codex profiles and
generates the plugin packages and both catalogs from the Copilot profiles.
See its [maintenance instructions](https://github.com/thomasmartinsen/agents#maintaining-plugins).
Publish plugin changes in the agents repository before updating this catalog.
References follow `main`, not immutable release SHAs.

Copilot plugins preserve the original agents' tool restrictions and safety
boundaries; Codex skills express tool boundaries as instructions, not enforced
permissions.
They draft content and advice; they do not add account access, publish content,
send messages, or run background monitoring. Health Guardian does not provide
medical diagnosis or treatment. Some profiles include sensitive personal and
family context; review the source before sharing or changing repository access.
Existing personal or project agents with matching IDs take precedence.

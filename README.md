# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) presets for Roy's npm projects.

| Preset | What it does |
| --- | --- |
| `local>royeyal/renovate-config` | Monday-morning (UTC) schedule; all minor/patch updates grouped into one branch; versions must be 3 days old; lock file refreshed weekly; majors wait for approval on the Dependency Dashboard issue. stylelint + its configs, and eslint + `@eslint/*`, take majors together in one branch. Opens a PR per group. |
| `local>royeyal/renovate-config:automerge` | Add on top: minor/patch and lock file updates merge into the default branch **without a PR**, once the branch's checks pass. Only use it in a repo whose branches get a build check — with no check, Renovate never merges. |

A project opts in with a `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["local>royeyal/renovate-config"]
}
```

The Renovate GitHub App must be installed on **this repo too** — `local>` presets are read with
the app's own token, which only reaches repos it is installed on.

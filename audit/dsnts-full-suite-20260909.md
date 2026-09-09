# DSN full-suite verification — 2026-09-09

All nine scenarios passed the native Bun test suite, TypeScript check, formatting check, and ESM/declaration build. These are fork-only audit results, not new upstream submissions or a claim that upstream PR checks have changed.

Run: https://github.com/ugin-man/dsnts/actions/runs/34326082221

Workflow commit: `fc9dfd164404b07674a8b19948bebd362a5b31e5`

Audited base: `824919b9878ba3f592428bc586cf2c3ff2466cd0`

Runtime: Bun 1.4.2, Node v22.23.2, Ubuntu 24.04.4.

## Prerequisite and results

Every scenario applies the existing, still-unmerged demo-download fix from tscircuit/dsnts PR #14 (`15638f663b4d0ead5cd9116b1e6424f9bd2fa402`) to an ephemeral checkout. All seven demo files downloaded successfully and their SHA-256 hashes were identical across the nine scenarios. No test-runner substitutions, production mocks, test deletions, or snapshot rewrites were introduced by the audit.

| Scenario | Tests passed | Tests failed | Type / format / build | Job ID | Artifact ID |
|---|---:|---:|---|---|---|
| Base + #14 only | 75 | 0 | All pass | 102383548970 | 10093802259 |
| PR #18 + #14 | 87 | 0 | All pass | 102383548839 | 10093805490 |
| PR #19 + #14 | 88 | 0 | All pass | 102383548630 | 10093803882 |
| PR #20 + #14 | 83 | 0 | All pass | 102383549098 | 10093812097 |
| PR #22 + #14 | 80 | 0 | All pass | 102383549012 | 10093815612 |
| PR #23 + #14 | 92 | 0 | All pass | 102383548972 | 10093817460 |
| PR #24 + #14 | 85 | 0 | All pass | 102383548915 | 10093821071 |
| All six + #14 | 140 | 0 | All pass | 102383548895 | 10093829619 |
| All six + #13 + #14 | 146 | 0 | All pass | 102383548911 | 10093830322 |

The totals repeat shared baseline tests across scenarios; they are not a count of distinct tests or additional contributions. Each scenario ran `bun test`, `bun run typecheck`, `bun run format:check`, and `bun run build` after successful installation and demo acquisition. Each native suite included six existing SVG snapshots.

Combined-six logs: https://github.com/ugin-man/dsnts/actions/runs/34326082221/job/102383548895

Combined-six artifact: https://github.com/ugin-man/dsnts/actions/runs/34326082221/artifacts/10093829619

## Pinned PR heads

| PR | Verified head |
|---|---|
| #13 | `23f2247c1e3f1dbc3fe2cb2e4e86841e2f74f872` |
| #14 | `15638f663b4d0ead5cd9116b1e6424f9bd2fa402` |
| #18 | `321b34d2a129ac9c4b91e72200b883ee16088ba5` |
| #19 | `f094b1fab36c7381cf398dc44899a9821feba122` |
| #20 | `bcc93ecbbc3f88d0d7d4cb8692772bcffa222323` |
| #22 | `0ebc3db802a2e0af2d8df85421ead747f85a4ed2` |
| #23 | `30fb549b10ba85e1b68b1e335f9286043b5bf896` |
| #24 | `d520153b9a428aefc75f98cdd94be177168a276c` |

The workflow verifies fetched PR heads against these SHAs. Artifacts include per-command exit codes and raw logs, applied patches, resulting Git tree SHAs, fixture hashes, and installed package versions. Downloaded artifacts were verified against GitHub-reported SHA-256 digests.

## Limitations and repository changes

The actual submission branches do not include #14. This audit does not change their CI badges or claim that their unchanged workflows now pass. It supplies full-suite evidence with the prerequisite fix applied. Acceptance and merging remain upstream decisions. External DSN/CAD tools and interactive browser behavior were not tested. The four earlier locally prepared, unsubmitted patches are not included.

Initial audit run 34325947012 stopped in the audit harness because `bun pm ls` required a lockfile although this repository disables saving one. The harness was corrected to inspect installed manifests. Production patches and test assertions were unchanged; the successful run is 34326082221.

Only a new validation branch and this report were added to ugin-man/dsnts. No upstream main branch, existing PR branch, PR body, issue, or comment was modified. No package was published, PR merged, or bounty claimed.

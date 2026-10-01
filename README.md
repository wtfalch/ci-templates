# ci-templates

Reusable GitHub Actions workflows and a composite action, shared across the
wtfalch estate (see `.github/workflows/` and `.github/actions/`).

## Pinning a caller's `uses:`

Pin every reference to this repo to a commit SHA (`@<40-char-sha>`) or a
release tag (`@vN`) — never `@main`. `main` is mutable: a push to it changes
what every caller's CI runs on their very next run, with no rollback point.

```yaml
uses: wtfalch/ci-templates/.github/workflows/test-run.yml@<sha-or-tag>
```

A moving major tag (`@v1`, re-pointed on each safe release) is cheap to stay
current with; a commit SHA is the stronger guarantee, since it cannot be
repointed out from under a caller. Either is acceptable — `@main` is not.

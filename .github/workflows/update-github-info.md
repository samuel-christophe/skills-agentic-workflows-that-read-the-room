---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Update the GitHub Info website content for Mona using current official GitHub references.

## Research

1. Read `notes/mona-notes.md` and `site/content/github-info.md` with the GitHub repository API tools. Do not use the terminal, CLI, or sandboxed shell commands for repository guidance or reference files.
2. Read the public GitHub Agentic Workflows guidance with `web_fetch` at `https://github.com/github/gh-aw/blob/main/.github/aw/github-agentic-workflows.md`.
3. Fetch `https://github.blog/latest/` with `web_fetch`.
4. Fetch `https://github.blog/changelog/` with `web_fetch`.

## Update

Use the official GitHub Blog and Changelog pages to identify concise, practical updates that help developers learn GitHub faster. Preserve the site's existing editorial angle, cite the relevant source URLs, and update only `site/content/github-info.md` when the research supports a useful change.

After editing, review the resulting diff for accuracy, concise writing, and valid Markdown. Use the `create_pull_request` safe output to open a pull request for Mona to review. Do not write directly to `main`, merge the pull request, or make unrelated changes.
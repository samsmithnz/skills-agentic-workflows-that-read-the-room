---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
tools:
  edit: true
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
---

Update Mona's GitHub information page with useful recent news from official GitHub sources.

1. Read `notes/mona-notes.md` for Mona's editorial guidance.
2. Use web fetch to read `https://github.blog/latest/`.
3. Use web fetch to read `https://github.blog/changelog/`.
4. Update only `site/content/github-info.md` with concise, practical information that helps developers learn GitHub faster. Link each new item to its GitHub Blog or GitHub Changelog source.
5. Use the `create_pull_request` safe-output tool to open a pull request for Mona to review. Summarize the sources and changes in the pull request body. Do not write directly to the default branch.

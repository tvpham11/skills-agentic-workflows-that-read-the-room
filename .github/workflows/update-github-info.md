---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
engine:
  id: copilot
  model: gpt-4.1
  model-provider: github
  copilot-sdk: true
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    max: 1
    draft: false
---

# Update GitHub Info

Keep `site/content/github-info.md` current with concise, practical GitHub guidance for developers.

## Instructions

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use `web-fetch` to read https://github.blog/latest/, https://github.blog/changelog/, and https://awesome-copilot.github.com/workflows/.
3. Identify recent updates that are useful to developers and relevant to the existing homepage themes in `site/content/github-info.md`. Prefer a small number of high-value items over a broad digest.
4. Edit only `site/content/github-info.md`. Preserve its existing structure and themes. Keep summaries short and practical, and link each item to its original GitHub Blog, Changelog, or Awesome Copilot workflows source.
5. Do not invent details or add an item unless it is supported by the fetched source. If there is no worthwhile update, leave the file unchanged and do not open a pull request.
6. When you make a change, use the `create-pull-request` safe output to open one pull request for Mona to review. Summarize the changes and cite the source URLs in the pull request description. Never write directly to the default branch.

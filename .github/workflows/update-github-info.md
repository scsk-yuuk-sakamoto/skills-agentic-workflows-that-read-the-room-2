---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
---

# Update GitHub Info

Keep `site/content/github-info.md` current with practical, useful GitHub guidance for Mona's website.

## Instructions

1. Read `notes/mona-notes.md` and the current `site/content/github-info.md` before making changes.
2. Use web-fetch to read both https://github.blog/latest/ and https://github.blog/changelog/.
3. Select only recent stories that are useful to developers learning GitHub. Verify details against the fetched sources, avoid duplicating existing themes, and keep the page's summaries short and practical.
4. Update `site/content/github-info.md` in its existing style. Include source links for every change based on the GitHub Blog or Changelog, and preserve useful existing guidance that is still accurate.
5. Review the diff for accuracy, concise wording, and working source links. Do not modify unrelated files.
6. Open one pull request for Mona to review using the `create-pull-request` safe output. Explain the changes and list the source links in the PR body. Do not write directly to the default branch.
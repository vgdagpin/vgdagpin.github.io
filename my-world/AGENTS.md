# Repository Guidelines

## Project Structure & Module Organization

This directory contains a dependency-free static manga reader:

- `index.html` — all page structure, styling, and JavaScript behavior.
- `Images/` — manga artwork named sequentially from `01.png` through `11.png`.

There are currently no separate source, build, or test directories. Keep related UI code together in `index.html` unless the project grows enough to justify extracting `styles.css` or `script.js`. Add story pages to `Images/` using zero-padded numeric names so lexical and reading order remain aligned.

## Build, Test, and Development Commands

No package installation or build step is required.

- `python -m http.server 8000` — serve the directory locally.
- Open `http://localhost:8000/` — review the reader in a browser.
- `node -e "const fs=require('fs'); const h=fs.readFileSync('index.html','utf8'); const s=h.match(/<script>([\s\S]*?)<\/script>/); new Function(s[1]);"` — perform a basic JavaScript syntax check.
- `git status --short` — confirm which files will be committed.

Avoid validating through `file://`; a local HTTP server more closely matches GitHub Pages behavior.

## Coding Style & Naming Conventions

Use two-space indentation in HTML, CSS, and JavaScript. Prefer semantic HTML, descriptive camelCase JavaScript identifiers, and kebab-case CSS class names. Group CSS by component and keep custom properties in `:root`. Use `const` by default and `let` only for reassigned values. Preserve accessibility attributes, keyboard controls, reduced-motion support, and mobile swipe behavior when changing navigation.

Image references are case-sensitive on GitHub Pages. Match paths exactly, for example `Images/01.png`.

## Testing Guidelines

There is no automated test framework or coverage requirement. Before submitting changes:

1. Run the JavaScript syntax check.
2. Test previous/next buttons, arrow keys, swipe gestures, fullscreen, cover, and ending page.
3. Check desktop and narrow mobile layouts.
4. Confirm every image loads without console errors.

## Commit & Pull Request Guidelines

Recent commits use short, imperative summaries such as `Add interactive manga book reader`. Follow that pattern and keep each commit focused.

Pull requests should describe the user-visible change, list manual checks performed, and include screenshots or a short recording for visual or animation changes. Link related issues when applicable. Do not commit generated caches, local server files, or unrelated repository changes.

## Agent Workflow

After completing and verifying every repository update, commit the changed files and push the commit to the current branch's configured remote. Confirm the working tree is clean afterward. Do not include unrelated user changes in the commit.

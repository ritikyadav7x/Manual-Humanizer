# Manual Humanizer — Sentence-by-Sentence Writing Editor

A small browser app for revising text deliberately, one sentence at a time.

**Built with:** HTML, CSS, JavaScript, browser localStorage, the Datamuse synonym API, and an optional OpenAI API integration.

## Features
- Parse paragraphs into editable sentences
- Compare original and revised versions
- Track progress and navigate between sentences
- Find synonyms through Datamuse
- Optionally request AI-generated revisions with a user-provided API key
- Save editing progress locally and export revised text
- Switch light/dark themes

## Local setup
```bash
git clone https://github.com/TheRitikYadav/Manual-Humanizer.git
cd Manual-Humanizer
python3 -m http.server 8000
```
Visit http://localhost:8000. There is no required build step.

## Architecture
| File | Responsibility |
| --- | --- |
| `index.html` | Editing workspace and settings |
| `app.js` | Sentence parsing, editor state, synonym lookup, AI requests |
| `styles.css` | Responsive design and themes |
| `manifest.json` | Web app metadata |

## Privacy and security

**This is not a fully offline application.** Draft text and preferences are stored in the current browser's localStorage. Individual words are sent to Datamuse when requesting synonyms. The optional AI rewrite feature sends the selected sentence and instructions to OpenAI when activated.

**Important:** The current optional AI integration stores a user-supplied API key in browser localStorage and makes requests from the browser. That approach is unsuitable for shared or untrusted devices and is not recommended for a production deployment. Use a securely authenticated backend proxy instead. Never embed a personal API key in deployed source code.

## Limitations
The editor is a prototype without a backend account system. Browser-storage data can be cleared, and no automated reliability or security audit is claimed.

## Next steps
Move AI requests server-side, add automated tests and explicit data-retention controls.

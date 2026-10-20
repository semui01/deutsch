# Satzlupe

A one-page tool for German learners. Paste a German sentence (or two) and it gives you a learner-friendly analysis in six parts:

1. Overall meaning
2. Word-by-word analysis (gender, case, plural, verb forms)
3. Grammar and sentence structure
4. Modal particles and nuance (doch, ja, mal, halt, …)
5. Natural alternatives
6. Tone and context

Everything lives in [`index.html`](index.html). There is no build step and nothing to install.

## Two ways to use it

**Copy prompt.** The page fills your sentence into the analysis prompt. Press **Copy prompt** and paste the result into any Claude chat. This works everywhere and needs no key.

**Analyse in the page.** Press **Analyse** (or <kbd>Ctrl</kbd>/<kbd>⌘</kbd> + <kbd>Enter</kbd>). The answer streams into the page with a section menu, a word table and colour-coded noun genders.

- When the page is opened as a claude.ai artifact, it runs on the viewer's own Claude account. You don't need an API key.
- When it is opened anywhere else (a local file or GitHub Pages), it calls the Claude API directly from the browser with your own Anthropic API key (model `claude-opus-5-5`). The key is kept only in that browser and is sent only to `api.anthropic.com`.

On claude.ai the page can't contact `api.anthropic.com`, so API keys only work in the standalone page. If you share the artifact, each person who opens it uses their own Claude account and must be signed in. Anyone who would rather use their own API key should open `index.html` instead.

## Running it locally

Open `index.html` in a browser, or serve the folder:

```sh
npx serve .
```

To host it, turn on GitHub Pages for this repository (Settings → Pages → deploy from the branch root).

## Changing the prompt

The prompt template is the `buildPrompt()` function near the top of the script in `index.html`. **Copy prompt** copies exactly that text. **Analyse** sends the same text plus a short formatting note (Markdown headings, a word table) so the page can lay out the answer.

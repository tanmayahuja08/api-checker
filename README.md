# API Checker

Static, client-side-only API checker UI.

## How It Runs

- `index.html` contains the app UI, CSS, and JavaScript.
- Users can use View Source to read all client-side code.
- There are no external scripts or imported CSS files; the only separate files are static images.
- There is no backend, no Netlify Function, no build step, and no package install.
- API requests are made directly from the browser to the API Base URL entered in the page.
- API keys are not saved by the app; they stay in the current page input.

## Deploy To Netlify

1. Create a new Netlify site from this folder.
2. Use these settings:
   - Build command: leave empty
   - Publish directory: `.`
3. Deploy.

The included `netlify.toml` already sets those values.

## Important Browser Limitation

Some API providers block direct browser requests with CORS. If that happens, the static site is working, but that provider does not allow client-side calls from the browser.

## Airgapped Laptops

- If the laptop is airgapped, no request can reach hosted APIs such as OpenAI, OpenRouter, Groq, or Anthropic.
- Compatibility mode only changes request format and headers. It cannot bypass airgap, DNS failure, missing internet, blocked ports, or browser CORS.
- For airgapped use, run a local OpenAI-compatible server on the laptop or local network, then set Base URL to something like `localhost:11434/v1`, `localhost:1234/v1`, or your local server URL.
- The app debug log now explains whether a failure looks like offline/airgap, local server not running, CORS, authorization, missing path/model, or rate limiting.

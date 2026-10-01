# AGENTS.md

## Project Overview
Single-file static HTML app — an Albanian wedding invitation creator ("Ftesa Dasme"). No build step, no backend, no dependencies. All logic is vanilla JS in `index.html`, using `localStorage` for persistence.

## Running the App
- `docker compose -f docker-compose.base44.yml up -d`
- Served by nginx:alpine on host port 3000.
- The source is bind-mounted read-only; edits to `index.html` are reflected immediately (call `reload_preview` to see them in the preview).

## Known Quirk
- The sandbox directory `/app` has 700 permissions by default. nginx's worker runs as non-root and cannot traverse it. Fix with `chmod 755 /app` if the container returns 403.

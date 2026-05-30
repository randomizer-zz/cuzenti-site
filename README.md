# cuzenti.com

Static site for [cuzenti.com](https://cuzenti.com). Deployed on Netlify, auto-published from `main`.

## Pages

- `/` — marketing landing page
- `/privacy-policy` — privacy policy
- `/delete-account` — account-deletion request page (Play Store requirement)
- `/join/CODE` — invite landing page for room + league deep links (rewritten to `/join.html?code=CODE` via `netlify.toml`)

## Deep link infrastructure

- `.well-known/apple-app-site-association` — declares the iOS app's Universal Link routes (must be served as `application/json`, see `netlify.toml`)
- `.well-known/assetlinks.json` — Android App Links verification

Both reference `com.cuzenti.cuzenti` (bundle / package) and iOS Team `4MY9FG8QUH`.

If the release signing fingerprint or Apple Team ID changes, both files must be updated **and** Apple's CDN cache flushed (it caches the AASA for up to 24h).

## Deploy

Netlify watches `main` and rebuilds on push. There is no build step — `netlify.toml` sets `publish = "."` so the repo IS the deploy.

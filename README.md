# Stash — Umbrel App Store

The official [Umbrel Community App Store](https://github.com/getumbrel/umbrel-community-app-store)
for **[Stash](https://github.com/savewithstash/stash)** (`savewithstash-stash`) —
hoard everything, find anything: a private "save anything" inbox powered by
on-device QVAC models.

## Install on your Umbrel

1. In umbrelOS, open **App Store → ⋯ (top-right) → Community App Stores**
2. Add this repository's URL:

   ```
   https://github.com/savewithstash/umbrel-app-store
   ```

3. Open the **Stash** store and install the app.

## Publish / update flow (maintainers)

1. Build & push the arm64 image (from the [app repo](https://github.com/savewithstash/stash) root):

   ```bash
   docker buildx build --platform linux/arm64 -t savewithstash/stash:<version> .
   docker push savewithstash/stash:<version>
   ```

2. Bump `version:` in `savewithstash-stash/umbrel-app.yml` (plus `releaseNotes`)
   and the image tag in `savewithstash-stash/docker-compose.yml`, then commit &
   push this repo (must be **public**).

3. On the Umbrel: open the community store → **Update** appears on Stash.

## Notes

- First launch downloads ~1.3 GB of model weights into
  `${APP_DATA_DIR}/models`; notes are stored in `${APP_DATA_DIR}/data`.
- Needs an arm64 Umbrel (Raspberry Pi 4/5) with ≥4 GB RAM — 8 GB recommended,
  and required if you want the lazy-loaded vision model on top.

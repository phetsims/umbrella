# umbrella
Umbrella is a lightweight harness repo for PhET development. It checks out selected sims and common-code repositories into one workspace and provides npm scripts to clone, update, and run dev servers locally or in GitHub Codespaces.

## Quickstart
- `npm install` – clones base repos (`chipper`, `perennial-alias`) and installs their dependencies (only these two repos get `npm install` automatically).
- `npm run add-sim -- <sim-name>` – clones the sim plus its `phetLibs` and common libs listed in `chipper/build.json` (no auto-install in sims/libs).
- `npm start` – runs `npx grunt dev-server --port=8123` from `repos/chipper` to serve all sims; add at least one sim first.
- Clones are shallow (`git clone --depth=1 --single-branch`) to speed up large repos. If you need full history later, run `git fetch --unshallow` (and `git fetch origin --tags` if desired) inside the repo, or delete the repo and clone it manually without `--depth=1`.

## Maintenance scripts
- `npm run list-sims` – show tracked sims.
- `npm run pull-all` / `push-all` – pull or push all tracked repos.
- `npm run status-all` – show working copy status for all tracked repos.
- `npm run clean-all` – discard working copy changes (`git reset --hard` + `git clean -fd`).
- `npm run remove-sim -- <sim-name>` – remove a sim and prune repos no longer required by any remaining sims.

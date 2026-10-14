# Shoin-zukuri GitHub Pages mirror

An independent GitHub Pages copy of [Shoin-zukuri](https://github.com/ludwigpeking/Shoin_zukuri_WFC).
The original project remains the only source of application code.

## Deployment

Create a public repository named `shoin-zukuri-WFC` in the mirror organization,
push these files to `main`, and select **GitHub Actions** under **Settings → Pages**.
Leave the custom domain empty for both this repository and the organization site.
The mirror address is `https://rattenstadt-mirror.github.io/shoin-zukuri-WFC/`.
It will not redirect to the original site's custom domain.

The workflow checks the original project's `main` branch at minute 23 of each hour.
GitHub may delay scheduled runs. It builds and deploys when the source changes;
**Actions → Update Shoin mirror → Run workflow** also publishes immediately.
No personal access token, deploy key, or access to the original repository's settings is needed.

After a successful deployment, the workflow records its source commit and UTC month
in `deployed-state.txt`. A monthly refresh also updates this record when the source
has not changed, keeping the mirror repository active so GitHub does not disable
its schedule after 60 days of inactivity. The recording job can write only to this
mirror repository using its automatic, temporary GitHub token.
Unchanged hourly checks skip the build and deployment. Failed deployments leave
the previous successful site and record in place so the next check can retry.

The workflow refuses a build containing a `CNAME` file. Do not add a custom domain
to this organization or its Pages site, as that would defeat the independent address.

## Verification after publishing

- Open the mirror address and confirm it stays on `github.io`.
- Confirm the buildings, terrain, sky, and controls load without asset errors.
- Confirm the existing `www.rattenstadt.com/Shoin_zukuri_WFC/` page is unchanged.
- Run a fresh mainland China accessibility check against the mirror page and model.
  A successful probe does not guarantee access from every network or full 3D rendering.

## Rights

Application design, code, models, and images remain copyright Richard Qian Li.
See the original project's rights notice. This mirror is maintained on the author's behalf.

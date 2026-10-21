# SignalRank — AI Visibility Review

Single-offer affiliate review landing page, hosted free on GitHub Pages.

## Live site

`https://<github-username>.github.io/<repo>/`

## What's here

```
index.html                     the landing page (self-contained, no dependencies)
.github/workflows/deploy.yml   auto-deploy on every push to main
```

## Deploy

```powershell
# from the affiliate-engine folder
powershell -ExecutionPolicy Bypass -File scripts\deploy.ps1 -Repo <repo-name>
```

The script creates the repo, pushes, and turns on Pages. It refuses to run while
`{{OMNISEO_AFFILIATE_URL}}` is still a placeholder, so a broken CTA can never ship.

## Replace the affiliate link

Once OmniSEO approves the application and the Links tab unlocks:

```powershell
node scripts\build-links.mjs . "<your referral link>"
```

That regenerates `tracking/links.csv` and `tracking/links.md` with real UTM tags.
To update the landing page CTA, replace `{{OMNISEO_AFFILIATE_URL}}` in `index.html`
with the same link.

## Compliance

The page carries an FTC affiliate disclosure above the fold and again in the footer,
before the first affiliate link. Keep it that way — see
`docs/ACCOUNTS.md` and the FTC reference in the affiliate-skills pack.

## Built with

The [affiliate-skills](https://github.com/Affitor/affiliate-skills) pack
(`landing-page-creator` → `github-pages-deployer` → `conversion-tracker`).

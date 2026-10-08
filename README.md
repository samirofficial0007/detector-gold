# Magnetic Field Scanner

A static HTTPS website that reads the phone's `Magnetometer` sensor through the browser's Generic Sensor API.

## Important

This project detects **magnetic-field changes**. It does **not** detect or identify gold and it cannot reliably determine underground depth.

Your OPPO A15s (CPH2179) has an AKM09918C magnetometer, so the hardware is present. Browser support/permissions can still vary.

## Files

- `index.html` — complete frontend
- `render.yaml` — Render static-site configuration and the `Permissions-Policy` header

## GitHub + Render deployment

1. Create a new GitHub repository.
2. Put `index.html` and `render.yaml` in the repository root.
3. Commit and push to the `main` branch.
4. In Render: **New → Static Site**.
5. Connect the GitHub repository.
6. Branch: `main`
7. Build Command: leave empty.
8. Publish Directory: `.`
9. Create the site.
10. Open the generated `https://....onrender.com` URL on the Android phone.
11. Press **Start Scanner**.

Render provides HTTPS for static sites, which is important because browser sensor APIs require a secure context.

## Termux Git commands

Replace `YOUR_USERNAME` and `YOUR_REPO` with your GitHub details:

```bash
cd ~/magnetic-field-scanner
git init
git add .
git commit -m "Initial magnetic field scanner"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

If GitHub asks for authentication, use your normal GitHub authentication/PAT method.

## If it still says "Magnetometer API unavailable"

Check:

- Open the Render **HTTPS** URL, not `content://...`.
- Use an up-to-date Chrome on Android.
- Make sure the page is not inside an iframe.
- Check Chrome/site sensor permissions if a permission prompt appears.
- The browser may simply not expose the Generic Sensor API on that device/browser.

## No backend required

This is a static site. No Node.js, Python, database, or API is needed.

# DreamCine Production — GitHub Pages package

This package keeps the supplied DreamCine Production website design and admin features, with clearer GitHub media-storage wording.

## Files
- `index.html` — complete website.
- `data.json` — editable site content loaded by the website.
- `uploads/` — destination for media uploaded through the website's GitHub connection.
- `.nojekyll` — tells GitHub Pages not to run Jekyll processing.

## Publish on GitHub Pages
1. Create or open the GitHub repository for this website.
2. Upload **all files and folders in this package** to the repository root (not the ZIP itself).
3. Commit the files to the `main` branch.
4. In the repository, open **Settings → Pages**.
5. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
6. Wait for the Pages deployment and open the URL shown in Settings → Pages.

For a project repository, the site URL normally looks like `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/`. The site code supports a project path and lets you configure the repository and website file path in its Admin → GitHub panel.

## Connect the website's Admin panel to GitHub
1. Open the live website and choose **Admin**.
2. Create the first admin password when prompted.
3. Open the **GitHub** tab in the admin panel.
4. Create a fine-grained personal access token at https://github.com/settings/personal-access-tokens/new
5. Give it access only to this website repository and grant **Repository permissions → Contents → Read and write**.
6. Enter the repository as `OWNER/REPOSITORY`, branch `main`, website file path `index.html`, and paste the token.
7. Save the connection and use **Test** to verify it.

The token is stored in that browser's local storage for the admin connection. Do not paste it into `index.html`, `data.json`, a public issue, or a commit. Anyone who can access the browser profile and its local storage may be able to use it; disconnect it and revoke it in GitHub if that browser is shared or compromised.

## Media storage: important limits
- The website's GitHub upload code has a **99 MiB per-file cap** for video uploads. Photos are resized and converted to JPEG before upload.
- This is **not a 99 MiB total-site quota**. Multiple media files can make the repository exceed 100 MB in total.
- GitHub blocks regular Git files larger than 100 MiB and recommends keeping repositories small (ideally under 1 GB; 5 GB is strongly discouraged). For large media libraries, use object storage/CDN and keep only media URLs in `data.json`; do not use a Git repository as an unlimited media drive.
- GitHub's browser upload UI has a smaller per-file limit than Git's/API routes. Use the website's Admin → GitHub connection for supported uploads rather than relying on the browser's drag-and-drop uploader.
- GitHub Pages is static hosting. It does not provide PHP execution, a database, or private server-side storage. The `save.php` and `/api/*` fallbacks in the original site require a separate compatible backend; the GitHub Pages path uses the GitHub API connection for admin saves/uploads.

## Notes
- The initial site content is also embedded in `index.html` as a fallback. `data.json` is included so the site can load separately saved content on GitHub Pages.
- Keep the repository public if you are using the free GitHub Pages plan.

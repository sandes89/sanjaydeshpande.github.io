# Creating and Updating the Website Repository

This site is a static website. It has no build step, package installation, backend, or database. The GitHub repository should be named `sanjaydeshpande.github.io` and owned by the GitHub account `sanjaydeshpande`.

## 1. Create the GitHub repository

1. Sign in to GitHub as `sanjaydeshpande`.
2. Select **New repository**.
3. Set the repository name to **`sanjaydeshpande.github.io`**.
4. Choose **Public** so GitHub Pages can publish the personal site.
5. If the site files are already on your computer, create the repository without a README, license, or `.gitignore` to avoid an unrelated first commit.
6. Create the repository.

The personal-site repository name is special: it publishes at <https://sanjaydeshpande.github.io/>.

## 2. Add the website files the first time

### Option A — GitHub website upload

1. Open the new repository and choose **Add file → Upload files**.
2. Upload the contents of this website folder, including `index.html`, `styles.css`, `script.js`, `favicon.svg`, `.nojekyll`, and the `.github/workflows/pages.yml` workflow.
3. Keep the directory structure. In particular, `.github/workflows/pages.yml` must remain under `.github/workflows/`.
4. Enter a commit message such as `Add personal portfolio website`.
5. Commit directly to the `main` branch.

GitHub may hide dotfiles in file pickers. Confirm that `.nojekyll` and `.github/workflows/pages.yml` were included. If not, add them using GitHub's file editor or Option B.

### Option B — Git from a terminal

Open a terminal in this website folder. If it is not already a Git repository, run:

```sh
git init
git branch -M main
git add index.html styles.css script.js favicon.svg .nojekyll README.md REPOSITORY-GUIDE.md .github/workflows/pages.yml
git commit -m "Add personal portfolio website"
git remote add origin https://github.com/sanjaydeshpande/sanjaydeshpande.github.io.git
git push -u origin main
```

If Git reports that `origin` already exists, inspect it with `git remote -v` and update it only if it points to the wrong repository:

```sh
git remote set-url origin https://github.com/sanjaydeshpande/sanjaydeshpande.github.io.git
```

If this folder already contains a Git repository and a remote, do not repeat `git init` or `git remote add`; inspect with `git status` and `git remote -v` first.

## 3. Enable and verify GitHub Pages

1. In the repository, open **Settings → Pages**.
2. Under **Build and deployment**, select **GitHub Actions** as the source.
3. Open the **Actions** tab and wait for **Deploy static site to GitHub Pages** to complete successfully. The workflow runs on pushes to `main`.
4. Visit <https://sanjaydeshpande.github.io/>. The first deployment can take a few minutes.

If deployment fails, open the failed workflow run in **Actions**, inspect the failing step, and correct that issue before retrying. Do not copy deployment tokens into website files.

## 4. Update the website later

1. Edit the site files in the local website folder.
   - `index.html`: biography, career, education, publications, awards, patents, and profile links.
   - `styles.css`: colors, typography, spacing, and responsive layout.
   - `script.js`: optional mobile-navigation enhancement.
2. Preview the page locally in a browser and check both desktop and mobile layouts.
3. Check the change before publishing:

   ```sh
   git status
   git diff --check
   git diff
   ```

4. Stage only the intended site changes, then commit and push:

   ```sh
   git add index.html styles.css script.js favicon.svg
   git commit -m "Update portfolio content"
   git push
   ```

   Adjust the `git add` list to match the files you changed. For example, if you edit this guide or the workflow, include those paths too.
5. Check the **Actions** tab for a successful deployment, then refresh the live page. A hard refresh may be needed to bypass browser caching.

## 5. Updating safely

- Keep `index.html` in the repository root; GitHub Pages uses it as the homepage.
- Keep `.github/workflows/pages.yml` in place so pushes to `main` deploy automatically.
- Do not upload passwords, access tokens, private keys, or other credentials.
- Verify CV facts and publication citations before adding or changing them.
- If you add images or other files, use relative paths (for example, `images/portrait.jpg`) and commit those assets too.
- GitHub Pages serves static files only. Do not add server-side secrets or expect PHP, Python, or a database to run there.

## 6. If making a change directly on GitHub

For a small text change, open `index.html` in the repository, select the edit button, make the change, and commit it to `main`. For larger changes, edit locally so you can preview the result before pushing. Every commit to `main` triggers the Pages workflow.

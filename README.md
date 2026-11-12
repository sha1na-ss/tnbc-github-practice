# TNBC GitHub practice

Practice the workflow we use on the main project: **branch → commit → push → pull request → review → merge**.
Nothing here can break anything, so experiment freely.

## Before you start
1. Accept the collaborator invite (check your email, or github.com/notifications).
2. Install Git: https://git-scm.com/downloads
3. Tell Git who you are (once per computer):
   ```
   git config --global user.name "Your Name"
   git config --global user.email "the-email-on-your-github-account"
   ```

## Exercise 1: Your first pull request
1. **Clone** the repo and go into it:
   ```
   git clone https://github.com/OWNER/tnbc-github-practice.git
   cd tnbc-github-practice
   ```
2. **Make a branch** (never work on `main`):
   ```
   git checkout -b add-yourname
   ```
3. **Make your file:** copy `members/_template.md` to `members/yourname.md` and fill it in.
4. **Commit and push:**
   ```
   git add members/yourname.md
   git commit -m "Add yourname intro"
   git push -u origin add-yourname
   ```
   If Git asks you to sign in, a browser window should open. If it asks for a password in the terminal,
   your GitHub password won't work: install GitHub CLI (https://cli.github.com) and run `gh auth login`, then push again.
5. **Open a pull request:** on the repo page, click **Compare & pull request**. Give it a clear title,
   write one line on what you changed, and add **sha1na-ss** (or your buddy) as a **Reviewer** on the right.
6. **Respond to the review:** you'll get at least one comment. Make the change in your file, then:
   ```
   git add members/yourname.md
   git commit -m "Address review comments"
   git push
   ```
   The pull request updates by itself.
7. **Merge:** once it's approved, click **Merge pull request**, then **Delete branch**.
8. **Update your copy of main:**
   ```
   git checkout main
   git pull
   ```

## Exercise 2 (optional): Fix a merge conflict
1. Make a new branch: `git checkout -b team-yourname`
2. In `team.md`, add one line **directly under the heading**: `- Your Name: one word that describes you`
3. Commit, push and open a pull request, like in Exercise 1.
4. If someone else's line was merged first, GitHub will say **This branch has conflicts**. Fix it:
   ```
   git checkout main
   git pull
   git checkout team-yourname
   git merge main
   ```
   Open `team.md`, keep both lines, delete the `<<<<<<<`, `=======` and `>>>>>>>` markers, then:
   ```
   git add team.md
   git commit -m "Resolve merge conflict"
   git push
   ```

## Rules we follow on the real repo too
- Never commit straight to `main`. Every change goes through a pull request.
- One review before merging.
- Short branch names that say what you're doing: `add-ecg-filter`, `fix-display-bug`.
- Commit messages say what changed: "Add lead-off detection", not "update".

Stuck? Ask in the team channel. No question is too basic.

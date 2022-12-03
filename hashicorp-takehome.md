## Content

### What is the difference between push, pull, and fetch in Git?

- `git push` - send changes from a local branch to the corresponding branch in a remote repository
- `git fetch` - get changes from a remote repository into your local tracking branch
- `git pull` - get changes from a remote repository into your tracking branch and merge the changes into a local branch

Often, `git fetch` and `git pull` are described as the same. This isn't entirely correct, since under the hood `git pull` does two things, while `git fetch` does only one. `git fetch` takes your current branch, and checks to see if there is a tracking branch. If so, it looks for changes in the remote repository branch, and pulls them into the tracking branch. It does not change your local branch. To do that, you'll need to do `git merge origin/main` (for the "main" branch) to merge those changes into your branch - probably also called "main".`git pull` simply does a `git fetch` followed immediately by `git merge`. This is often what we want to do, but some people prefer to use `git fetch` followed by `git merge`. They do this to understand the changes they are merging into their branch before the merge happens.

`git push` is different from both `git fetch` and `git pull`. `git push` takes your current branch, and checks to see whether or not there is a tracking branch for a remote repository connected to it. If so, it takes your changes from your branch and pushes them to the remote branch. `git push` is how you share your local code with a remote repository. You can think of `git push` as making the remote branch resemble your local branch. `git push` fails if the remote branch has diverged from your local branch. Divergence happens when there are commits in the remote branch not reflected in your local branch. If this happens, synchronize your local branch with the remote branch using `git pull` or `git fetch` and `git merge`.

---
title: Opening a Pull Request Against an Existing Pull Request
---

**NOTE: This document is a work in progress**

First clone you fork and set it up to track both the `redhat-cop` project and the `etsauer` forks.

```
git clone git@github.com:myuser/openshift-playbooks.git
cd openshift-playbooks/
git remote -v
  origin	git@github.com:my-user/openshift-playbooks.git (fetch)
  origin	git@github.com:my-user/openshift-playbooks.git (push)
git remote add upstream git@github.com:redhat-cop/openshift-playbooks.git
git remote -v
  origin	git@github.com:my-user/openshift-playbooks.git (fetch)
  origin	git@github.com:my-user/openshift-playbooks.git (push)
  upstream	git@github.com:redhat-cop/openshift-playbooks.git (fetch)
  upstream	git@github.com:redhat-cop/openshift-playbooks.git (push)
git remote add etsauer git@github.com:etsauer/openshift-playbooks.git
git remote -v
  etsauer	git@github.com:etsauer/openshift-playbooks.git (fetch)
  etsauer	git@github.com:etsauer/openshift-playbooks.git (push)
  origin	git@github.com:my-user/openshift-playbooks.git (fetch)
  origin	git@github.com:my-user/openshift-playbooks.git (push)
  upstream	git@github.com:redhat-cop/openshift-playbooks.git (fetch)
  upstream	git@github.com:redhat-cop/openshift-playbooks.git (push)
```

Now we can create a new branch to track an existing branch from `etsauer`'s fork.

```
git fetch etsauer
...
 * [new branch]      new-install-guide -> etsauer/new-install-guide
...
git checkout -b my-new-pr-branch
  Switched to a new branch 'my-new-pr-branch'
git rebase etsauer/new-install-guide
  First, rewinding head to replay your work on top of it...
  Fast-forwarded my-new-pr-branch to etsauer/new-install-guide.
```

Next we make our changes, and then push our new branch.

```
git add somefile
git commit -m"Making some changes"
git push -u origin my-new-pr-branch
```

Now we can navigate to our fork in GitHub, and select *New Pull Request*. Select the fork you want to merge to (`etsauer`) as the _base fork_ and select YOUR fork and branch as the head fork.

## Done!

* [Back to Start](./index.html)

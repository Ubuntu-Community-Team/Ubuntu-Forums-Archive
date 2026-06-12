---
title: "universe repository"
date: 2005-10-18
forum: Desktop Environments
---

### Post by str on 2005-10-18
is it safe to turn on the universe repository?

---

### Post by Perfect Storm on 2005-10-18
Aye, I have not heard or experienced any problems with it.

---

### Post by mpettitt on 2005-10-18
Should be. You might get a few issues with some programs since the testing procedure is a bit less strict, but I've not noticed any major problems and have been using universe since Warty...

---

### Post by str on 2005-10-18
how about backports?

---

### Post by str on 2005-10-18
when I'm doing apt-get update, i'm getting the following:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

What could be the problem?

---

### Post by mpettitt on 2005-10-18
Now that can cause problems, as happened with the Firefox 1.0.7 upgrade a little while ago. Still, 90% of the time, they work perfectly. It depends if you are confident enough to fix any problems that occur, and how important the latest packages are to you.
If you're running Breezy, there isn't much point with backports at the moment - the packages are already pretty much up to date.

The index files problem is probably just a temporary issue with the repository server. Give it a few minutes and try again.

---


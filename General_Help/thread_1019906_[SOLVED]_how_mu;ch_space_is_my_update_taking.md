---
title: "[SOLVED] how mu;ch space is my update taking?"
date: 2008-12-23
forum: General Help
---

### Post by cknight on 2008-12-23
Using the command line I did the following:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

Haven't done it in awhile so it identified 49 packages to upgrade.  Fine and dandy.  However, it also says the following:
```
49 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 46.2MB of archives. After unpacking 131kB will be used.
```

Why is it downloading 46MB, but only using 131kB of disk space?  Or do I have this completely wrong?  What am I missing here?

---

### Post by taurus on 2008-12-23
Because updater will remove the older versions that the new packages replace.

---

### Post by cknight on 2008-12-23
> **taurus said:**
> Because updater will remove the older versions that the new packages replace.

Haha, duh.  Thanks for pointing out what should have been obvious.

---


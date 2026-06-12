---
title: "After change home folder I can't find old home to delete &amp; I must to install old app"
date: 2016-02-19
forum: Desktop Environments
---

### Post by onracings on 2016-02-19
I change home folder by:
create new user
use command: sudo usermode -d /new-home-forder username
the home folder changed but:
I can't old home folder to delete and some app need to redownload and reinstall. I don't want that, how can I solve this?

---

### Post by buzzingrobot on 2016-02-19
"man usermod" says the "current home folder will be **moved**..."

A "move" is not a copy. When something is moved from its original directory to another directory, it no longer exists  in the original directory.

---


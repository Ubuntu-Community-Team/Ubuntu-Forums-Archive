---
title: "[SOLVED] remove a DE installed with apt-get"
date: 2008-06-29
forum: Desktop Environments
---

### Post by sisco311 on 2008-06-29
I can use tasksel --task-packages *DE-name*-desktop(ex. xubuntu-desktop) to list the packages that are part of the *DE-name*-desktop.

It's safe to remove the packages with
```
EDIT1: CODE REMOVED
``` or will this remove other important packages?

EDIT2: it's not safe.

---

### Post by .nedberg on 2008-06-29
Try ```
apt-get autoremove xubuntu-desktop
``` if you want to remove the xubuntu-desktop

---


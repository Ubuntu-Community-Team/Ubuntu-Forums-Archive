---
title: "Lost my toolbar/system tray - Kubuntu KDE 4"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Clark Nova on 2008-05-07
II installed the KDE 4 desktop environment for Kubuntu 8.04 and made a few changes to my visual settings. Upon restart my toolbar and system tray had vanished! Anybody got any ideas how I can get it back?

---

### Post by Clark Nova on 2008-05-08
Anybody got any ideas?:confused:

---

### Post by hermes0710 on 2008-05-08
Try <alt>+F2 and type "kicker"

---

### Post by Xiong Chiamiov on 2008-05-08
As always, you can do a
```

cd ~
mv .kde4 .kde4_old

```
to move your kde4 folder to a different name (effectively deleting it without losing it).  When you log back in again, KDE will regenerate a new .kde4 folder, and you can copy files back into the new folder until you find the problem.  It takes a while, but through a process of narrowing things down, you can find any problem with your KDE configs that way.

---


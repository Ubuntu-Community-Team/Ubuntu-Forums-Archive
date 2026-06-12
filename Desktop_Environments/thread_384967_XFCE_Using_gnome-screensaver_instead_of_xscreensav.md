---
title: "XFCE: Using gnome-screensaver instead of xscreensaver"
date: 2007-03-15
forum: Desktop Environments
---

### Post by satellite360 on 2007-03-15
Hi all

Is it possible to use **gnome-screensaver** instead of **xscreensaver** in Xfce 4.4?  I tried to follow [this guide]("http://www.linuxquestions.org/questions/showthread.php?t=458516") but when I try to remove **xscreensaver** I am warned that **xubuntu-desktop** will also be removed.

Thanks

---

### Post by louis_nichols on 2007-03-15
That's alright. Removing the package xubuntu-desktop won't uninstall your desktop environment. The package is just a metapackage, which means its only purpose is to depend on all the packages that make up the xubuntu desktop environment. So it is safe to uninstall.

---

### Post by satellite360 on 2007-03-15
Thanks Louis.

For anyone who wants to set up a panel launcher for the screen lock in gnome screensaver you will need the following command:
**gnome-screensaver-command --lock**

---

### Post by sardion on 2007-03-28
WARNING:

Removing xubuntu-desktop may break upgrades (i.e. from edgy to feisty).

---


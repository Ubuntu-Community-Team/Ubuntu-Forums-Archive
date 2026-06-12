---
title: "can only login Gnome with failsafe; KDE is fine"
date: 2007-06-07
forum: Desktop Environments
---

### Post by jbayone on 2007-06-07
For about a week now, I can only login to Gnome with the failsafe option.  Whenever I try to login normally, it just hangs on the screen with the tan background.  I've installed KDE since then, and it has no problem starting.

---

### Post by PointSource on 2007-06-08
Try deleting the file ~/.gnome2/session. This deletes a startup config file that may have an application in it that causes GNOME to hang. If you don't want to lose those settings, you will need to enable those programs one by one until one decides to hang. Also try to remember what specifically you did to the system before it stopped functioning normally.

---


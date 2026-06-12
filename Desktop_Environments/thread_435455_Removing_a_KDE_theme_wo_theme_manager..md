---
title: "Removing a KDE theme w/o theme manager."
date: 2007-05-06
forum: Desktop Environments
---

### Post by negat on 2007-05-06
For some reason I can not remove themes from KDE in Kubuntu Fiesty via the theme manager.  Is there any other way to remove it?

---

### Post by bunker on 2007-05-08
Theme manager themes are usually installed here: ~/.kde/share/apps/kthememanager/themes

Otherwise, they will be in /usr/share/apps/kthememanager/themes/ (which of course you need root privileges to delete from - maybe that's the problem?)

Delete the files with the relevant names and you should be sorted.

---


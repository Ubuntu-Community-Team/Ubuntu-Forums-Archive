---
title: "Unable to save bookmarks"
date: 2009-02-19
forum: Desktop Environments
---

### Post by Name141 on 2009-02-19
I'm getting this error message when closing a dolphin window "Unable to save bookmarks in /home/n/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive." yet I have over 90 GBs left.

---

### Post by krazyd on 2009-02-19
Are you using 8.04 / KDE4.1?

This bug was caused by the non-standard install directory of kde4 in hardy if I recall.

---

### Post by Name141 on 2009-02-20
Hardy.  However, I found the issue to be that root some how got the owner of the file.  I chowned it back to my normal user.  And it's still the KDE that came with hardy.

---


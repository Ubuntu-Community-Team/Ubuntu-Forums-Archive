---
title: "[SOLVED] Installing Theme"
date: 2007-10-22
forum: Desktop Environments
---

### Post by f37u5g0d on 2007-10-22
I am trying to install a theme.  I downloaded it from gnome-look.org and the instructions on that site say to unpack the files I downloaded and then move the files into /usr/share/themes on the filesystem.  I tried to do that and apparently I don't have permissions to write on the filesystem drive.  I can read only.  What do I do?

---

### Post by tropcky on 2007-10-22
just download a tar.gz theme   it gonna be more easyer for u to install it from the themer

---

### Post by NilsE on 2007-10-22
> **f37u5g0d said:**
>   I can read only.  What do I do?

In a terminal run: gksudo nautilus

This will put your file browser in root and then you can browse to the archive. Open it and then you should be able to install by extracting (with recreate folder on) it to the theme folder.

---

### Post by f37u5g0d on 2007-10-22
Hey thanks so much!

---


---
title: "KDE Style Update Issue"
date: 2007-03-26
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-03-26
Hi there,

After performing a routine update KDE lost Plastik (and various other styles). Is anyone else experiencing this problem? Any workarounds?

---

### Post by GS2 on 2007-03-26
I too updated, and looks like those styles have gone - off to Google to get them back :confused:

Edit>>

Styles left:
CDE
Motif
Motif Plus
Windows 9x
Platinum
SGI

---

### Post by GS2 on 2007-03-26
Still have no idea why some styles have been disabled (it seems the files are still resident in the directory trees), unless there have been problems with sigterm issues (a complete guess)

I use polyester style, and got around the problem be installing a different version 0.99+1.0b1-0ubuntu1_386.deb package for polyester styles from Kubuntu universe repository:

[http://archive.ubuntu.com/ubuntu/pool/universe/p/polyester/](http://archive.ubuntu.com/ubuntu/pool/universe/p/polyester/)

I could not find Plastik style in that repository, but if you have a look through this site:
[http://www.kde-look.org/](http://www.kde-look.org/)

You may be find a suitable style that works correctly

---

### Post by Jucato on 2007-03-26
This is a known issue due to an upgrade of Qt 3 packages on Feisty earlier. It has been fixed now and another set of Qt updates have been made available to fix this.

---

### Post by ShareBuntu on 2007-03-27
> **Jucato said:**
> This is a known issue due to an upgrade of Qt 3 packages on Feisty earlier. It has been fixed now and another set of Qt updates have been made available to fix this.

I'll update later today and see if it fixes the problem.

---

### Post by ShareBuntu on 2007-03-27
Yup, updating fixed it. :)

---


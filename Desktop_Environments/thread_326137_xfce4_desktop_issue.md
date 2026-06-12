---
title: "xfce4 desktop issue"
date: 2006-12-27
forum: Desktop Environments
---

### Post by case1976 on 2006-12-27
Hi All.

I am currently running ubuntu edgy + x windows system + xfce4.4-RC1 (the binary xfce4 package from repositories)

And i also tried to install xfce4.4-RC2 directly from xfce website, using the graphical installer. Everything went fine, except one small problem with desktop: when i create some item on desktop, and then delete it - formally it works as expected -  the item appears in the trash and in thunar i can see that the item has been removed from desktop. BUT ! - the item visually remains on the desktop, i mean the desktop icon remains on its place, whereas the file itself is removed !

I know that it's not a serious thing, but it makes me nervous though :)
Maybe anybody has a clue, how to make the desktop work correctly?

---

### Post by case1976 on 2006-12-27
I have solved the problem: before running xfce-installer one must install devel packaged for gamin (libgamin-dev  -- or something of this kind). Then the desktop works as expected after the installation.

---


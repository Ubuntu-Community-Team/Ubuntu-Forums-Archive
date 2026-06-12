---
title: "Remove Gnome Desktop from Ubuntu?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by wincen on 2006-08-26
I installed kubuntu-desktop with apt-get onto my ubuntu 6.06 computer.  I like kde and want to remove gnome desktop.  When I type sudo apt-get remove ubuntu-desktop i get an error saying ubuntu-desktop not installed.  how do i remove gnome desktop?

---

### Post by syadnom on 2006-08-26
apt-get install ubuntu-desktop

apt-get remove ubuntu-desktop

--
when you first install ubuntu, i does not install the meta-package ubuntu-desktop.  if you install this package then you can uninstall it.  also, you may end up updating some of the gnome packages but thats the price you pay.

good luck

---


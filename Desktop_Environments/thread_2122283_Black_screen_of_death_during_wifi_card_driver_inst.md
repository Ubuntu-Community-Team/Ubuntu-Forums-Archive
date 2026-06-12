---
title: "Black screen of death during wifi card driver install(12.04)"
date: 2013-03-04
forum: Desktop Environments
---

### Post by Pally1 on 2013-03-04
After which system wil not install anything at all and gives this error:

 Another application seems to be using the package system at this time. 
You must close all other package managers before you will be able to install or remove any packages.


tried every single thing i could find on the internet, nothing works, eventually everything leads to sudo dpkg --configure -a, but once i use it, i believe it attempts to reinstall wifi card driver and instantly leads to black scren of death.


Now i cant installany program at all, cant install updates or anything else.

Can someone please help find a solution for this?

Thank you!

---

### Post by Pally1 on 2013-03-04
Managed to solve it myself by teleting lock file in /var/lib/dpkg/    , and deleting everything in /var/lib/dpkg/update/

---

### Post by Pally1 on 2013-03-04
Actually it didnt help, it only made things much much worse =[.

Now i get black screen of death every time i try to install anything at all.

What is going on? Can someone please help?

---

### Post by Pally1 on 2013-03-04
These cursed files have reappeared themselves in dpkg and update. ne of them is lock file and two files in update.

One of the files in update cintains info on this broken driver that tries to install itself.


Package: bcmwl-kernel-source
Status: install ok half-configured
Priority: optional
Section: admin
Installed-Size: 3570
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bcmwl
Version: 6.20.155.1+bdcom-0ubuntu0.0.1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>



How do i stop my system from trying to install this crap and interrupting dpkg?

---


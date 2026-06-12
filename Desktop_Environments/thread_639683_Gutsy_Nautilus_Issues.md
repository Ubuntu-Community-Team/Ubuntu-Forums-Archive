---
title: "Gutsy Nautilus Issues"
date: 2007-12-13
forum: Desktop Environments
---

### Post by bistros on 2007-12-13
All:

I'm running Gutsy on an AMD64 with Nvidia GeForce 5500.  I'm using the proprietary Nvidia driver.

Basic installation went okay on this box, but there are Nautilus problems - here is a partial dump of nautilus-debug-log:

===== BEGIN MILESTONES =====
0x756640 2007/12/13 00:24:44.9367 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x756640 2007/12/13 00:24:44.9368 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x756640 2007/12/13 00:24:44.9368 (GLog): Can not get _NET_WORKAREA
0x756640 2007/12/13 00:24:44.9368 (GLog): Can not determine workarea, guessing at layout
0x756640 2007/12/13 00:25:30.7474 (USER): debug log dumped due to signal 11
0x756640 2007/12/13 00:25:30.7475 (USER): debug log dumped due to signal 11


Basically, the WM is not responding to Nautilus' request for info about the workspace.  This is a standard install with GDM as display manager and compiz as WM.

Without Nautilus running properly, many of the file management tools are blowing up.

I can supply xorg.conf, dmesg and any other debug info as required.

Cheers

---


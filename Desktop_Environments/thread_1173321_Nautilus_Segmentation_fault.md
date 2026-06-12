---
title: "Nautilus Segmentation fault"
date: 2009-05-29
forum: Desktop Environments
---

### Post by timosborn on 2009-05-29
I using the Gnome desktop with Ubuntu 9.04.  Everthing was working pretty well, until yesterday. Now nothing shows on my desktop, except the background. The panels at the top and bottom of the screen show and work. If I try and open a directory it says it is starting and then I get nothing. If I use gnome commander it works fine. If I try to run Nautilus from a terminal, I get this message: "Segmentation fault"

The log file reports:" May 29 09:58:28 big-black kernel: [ 6245.205490] nautilus[5560]: segfault at a110008 ip b5c76dc6 sp b5462fb0 error 4 in libbrasero-media.so.0.1.1[b5c65000+1f000] "

Any Ideas???  Thanks.

---

### Post by timosborn on 2009-06-24
This only seems to happen when there is a cd in the CD-RW drive.  The DVD-ROM does not affect Nautilus like this.

---

### Post by robtuk on 2009-06-25
seems to be a problem with libbrasero-media. I uninstalled this (along with brasero) which temporarily solves the problem, but no Brasero now.

Bug appears to have been [filed]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/337160") but can't see any recent updates to it.

---

### Post by timosborn on 2009-06-27
Thanks for the link to the bug report robtuk.  I think I'll drop brasero for now and follow the progress of the fix.

---


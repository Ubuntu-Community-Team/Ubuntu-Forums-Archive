---
title: "Printing Never Ends ;-)"
date: 2005-05-04
forum: Desktop Environments
---

### Post by carney1979 on 2005-05-04
Fresh install of Hoary on a i386 box.

Setup my printers as I have many times in the past with this computer using earlier versions of Warty and Hoary.

Printing works well EXCEPT the little printing icon in the taskbar never goes away when the job is complete.

Even though the job has completed, Hoary/Cups still thinks is is going on. I have to manually cancel each job after it has finished, no matter which printer I use.

How do I correct this?

David

---

### Post by yabbadabbadont on 2007-07-17
I apologize for resurrecting an ancient thread, but I am seeing the exact same behavior on an up to date Feisty install.  I don't have Gnome or KDE installed.  I use the web interface to CUPS.  It doesn't matter if I print to my Brother HL-1440 laser (connected through parallel port) or to cups-pdf virtual printer.  In either case, the job actually prints, but CUPS never detects that it has completed and spikes the CPU to near 100% until I cancel the job.  At first, I thought that the parport_pc module was not using either EPP or ECP mode to talk to the printer so that it could get the status read back, but dmesg output shows that it is using ECP.  Then I tested using the cups-pdf virtual printer.  The exact same thing happens...  very weird.  Any suggestions on how to trouble shoot this issue would be greatly appreciated.

---

### Post by yabbadabbadont on 2007-07-18
Bump.

Any trouble-shooting ideas are welcome.  :D

---

### Post by yabbadabbadont on 2007-07-19
Well, as an extreme trouble-shooting measure, I have done a complete reinstall and used all the defaults.  Now that I have the full ubuntu-desktop, I'll see if I can recreate the issue.  Hopefully, I won't be able to.  ;)

---


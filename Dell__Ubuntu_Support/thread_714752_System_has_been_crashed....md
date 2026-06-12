---
title: "System has been crashed..."
date: 2008-03-04
forum: Dell  Ubuntu Support
---

### Post by zeroed on 2008-03-04
Hi everybody.

Yesterday I reinstalled Ubuntu.
Laptop - Dell Inspiron 1501.
There is very helpfull site, ubuntu1501.com. Last time, when I installed ubuntu, I used articles from it and have installed all I need successfully.

This time I decided to do the same:
The last I have done before the crash was:
[http://www.ubuntu1501.com/2007/11/fix-for-gutst-taking-forever-to.html](http://www.ubuntu1501.com/2007/11/fix-for-gutst-taking-forever-to.html)

Two month ago, all was ok!

This time system has restarted and I so the following:

```
Starting up ...
[   0.356000] MP-BIOS bug: 8254 timer not connected to IO-APIC
[   0.488000] PCI: BIOS BUG #81[49435000] found
[   0.512000] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   0.512000] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
Loading, please wait...
```

Probably, this is not the problem itself. 
After that computer is not responding for a long time (2-3 minutes).
After that:

```
Check root=bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/d8a5b595-6ac0-4939-883d-1888b6daaf06 does not exist. Propping to a shell!
BusyBox v1.1.1 (Debian 1:1.1.3-5 ubuntu7) Build-in shell (ash)
Enter 'help' for a list of build-in commands.
(initramfs)...
```

What have a done before that patch:

1. Installed ubuntu.
2. Unchecked **all** repositories in source list.
3. Completly updated system.
4. Installed automatix, some software.
5. Updated system again, according to new software.
6. Installed proprietary ATI driver and compiz on XGL, as described in the following link: [http://www.ubuntu1501.com/2007/11/compiz-fusion-with-xgl-in-gutsy.html](http://www.ubuntu1501.com/2007/11/compiz-fusion-with-xgl-in-gutsy.html)
7. And finally this last patch.

Regards,
Denis.

---


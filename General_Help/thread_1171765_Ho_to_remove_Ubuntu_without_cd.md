---
title: "Ho to remove Ubuntu without cd"
date: 2009-05-27
forum: General Help
---

### Post by I-need-help on 2009-05-27
I need some help.
i have installed ubuntu netbook remix and i cannot remove it.
I do not have a cd-rom and i have tried acer e-recovery.

---

### Post by doas777 on 2009-05-27
> **I-need-help said:**
> I need some help.
i have installed ubuntu netbook remix and i cannot remove it.
I do not have a cd-rom and i have tried acer e-recovery.

well, you can boot a live-USB drive and use gparted to remove the ubuntu partition(s). if you need to add a windows MBR, you can find the instructions here: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
ms-sys is no longer in the repos, but you can find it with google, and install with a double-click.

or you can just boot from an installer for another OS (via netshare or whatever) and use it to repartition the disk during install.

the acer e-recovery requires a recovery partition. did you perhaps delete that partition when you isntalled ubuntu? you can look at your partitions with gparted to check.

---

### Post by philcamlin on 2009-05-27
when your installing a new os format it :popcorn:

---


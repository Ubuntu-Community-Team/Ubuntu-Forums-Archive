---
title: "No Ubuntu on a RAID0 system?"
date: 2009-02-21
forum: General Help
---

### Post by Cr4z33 on 2009-02-21
It is not 100% clear to me if I can or I cannot install Ubuntu Desktop 64 Bit v8.10 on a computer with a RAID0 system?
I have two Vista NTFS partitions and tried running WUBI, but after reloading and choosing to load Ubuntu it froze sadly at the loading screen.
I tried then the Alternate CD installation, but it got stuck at the partition screen.
So, no Ubuntu for my computer at this time? :(

---

### Post by Cr4z33 on 2009-02-23
Anybody knows it?

---

### Post by fjgaude on 2009-02-23
I would say it can be done, but we all will have to learn lots more than we presently know.

Take a look at what raid0 really is:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

Ubuntu has no way of knowing how to sync the two drives, each having half the data. If one drive fails you lose everything.

---

### Post by Cr4z33 on 2009-02-23
Yeah I know what RAID0 is and how fragile it can be.
That's why I daily backup my partitions. ;)
Thanks for the reply, but I better prefer not to install Ubuntu yet and keep my crap Vista.
In the meanwhile I will run Ubuntu with WMware.

---


---
title: "preventing partition mount"
date: 2006-02-15
forum: Desktop Environments
---

### Post by hunteramor on 2006-02-15
I know I should know the answer to this, but bear with me please  :D 

I don't want Linux to automatically mount one of my partitions (the NTFS one) at startup.  It pops up on the desktop, and I don't plan on using NTFS from linux, so I'd rather it didn't mount at all.

Here's the output from fdisk -l

> Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4863    39062016   83  Linux
/dev/hda2            4864        4985      979965   82  Linux swap / Solaris
/dev/hda3            4986       14711    78124095    7  HPFS/NTFS

Disk /dev/sda: 4095 MB, 4095737856 bytes
255 heads, 63 sectors/track, 497 cylinders

how can i prevent ubuntu from mounting hda3 every time i start up?

---

### Post by hunteramor on 2006-02-15
ok, deleting the hda3 line from my /etc/fstab file seems to have worked.  let me know if that's not a good way to do it, but it no longer is getting mounted.

---


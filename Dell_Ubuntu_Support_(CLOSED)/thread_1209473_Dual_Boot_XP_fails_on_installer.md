---
title: "Dual Boot: XP fails on installer"
date: 2009-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arshomette on 2009-07-10
I am trying to install Windows XP on a Studio 15 (Inspiron 1515) on another partition I have already resized.  I followed the instructions on this site: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")
But, when it comes time to install Windows, I get a fatal error (a la blue screen of death) after the message "Starting Windows" at the bottom.

Any help would be appreciated.

Useful (I think) outputs:
fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18957   152272071   83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda3           18958       29164    81987727+   7  HPFS/NTFS
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Let me know if I need anything else. Thanks.

---


---
title: "Noob: live USB boot- how to mount booted USB flash drive?"
date: 2009-05-31
forum: General Help
---

### Post by jorx on 2009-05-31
Hi all,
I'm trying out Linux Mint at the moment- and I have an issue where after booting up off of USB- my USB flash drive is mounted under  " /CDROM ".  The only problem is- /CDROM is read-only, so I can't transfer to or from the boot USB I used to boot up on.  

Now this wasn't an issue on a different distro I used- so I know it's possible to fix. But I'm quite new in regards to Linux- so advice would be appreciated! 

- so can I make /CDROM not "read-only" so I can write to it like a normal folder?

- or perhaps could I mount the USB drive somehow?

Thanks!

---

### Post by dmizer on 2009-06-01
Please post the results of:
```
sudo fdisk -l
```

---

### Post by jorx on 2009-06-03
Disk /dev/sda: 160.0 GB, 160041885696 bytes                       # This looks like the computer's hard drive
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79dcacf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16013852672 bytes                          # This is my startup USB flash drive
78 heads, 13 sectors/track, 30845 cylinders
Units = cylinders of 1014 * 512 = 519168 bytes
Disk identifier: 0x0003557e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           8       30846    15634496    c  W95 FAT32 (LBA)






Yeah- when I'm looking at the different drives- they show up- like "160.0 GB Media" and "CD-RW" and "USB Drive" next to "Filesystem".
But probably the USB drive and CD Drive aren't mounted properly, because I go into the filesystem, and my usb startup flash drive is mapped to /CDROM (and read only).

---

### Post by jorx on 2009-06-15
*bump*

I'm still struggling with this issue- of my bootup USB flash drive being mounted under /CDROM and being read-only.

---


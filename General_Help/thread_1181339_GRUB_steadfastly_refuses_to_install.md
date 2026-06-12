---
title: "GRUB steadfastly refuses to install"
date: 2009-06-07
forum: General Help
---

### Post by ncalvin on 2009-06-07
Note: this is a copy from a post in the Install & Upgrade forum

Today I decided to make a new partition in my internal HDD for my desktop for the purpose of running Jaunty. I attempted to install from the CD, and things ran dandy until 94%, at which point an error message told me that GRUB failed to install, and that this was a fatal error.

So I tracked down some solutions on my laptop whilst running Ubuntu from the CD on my desktop. I have come across multiple "solutions", none of which have fixed the problem.
"find /boot/grub/stage1 yields an Error 15
"find /grub/stage1" has the same result.
I tried the SGD and got a variety of error messages.

As for my setup, I am running Vista 64-bit on a 1TB partition, with the rest of the 1.5TB drive split off for Ubuntu. I also have a 1TB external connected via e-SATA (though I doubt this is relevant). I'm running in circles, making no progress, and am frankly completely fed up. It would appear that GRUB simply cannot be installed on my system.

If anyone has a viable solution, I'd love to hear it. I had no such issues a couple of years ago running Feisty on Vista 32.

---

### Post by ncalvin on 2009-06-07
...hi?

---

### Post by VMC on 2009-06-07
from a terminal type this:

```
sudo fdisk -l
```

also is this on Ext4 file system?

---

### Post by ncalvin on 2009-06-07
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x067e7f80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ebf7bb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      132611  1065194492    7  HPFS/NTFS
/dev/sdb2          132612      182401   399938175    5  Extended
/dev/sdb5          132612      181177   390106363+  83  Linux
/dev/sdb6          181178      182401     9831748+  82  Linux swap / Solaris
```

And it's ext3

---

### Post by VMC on 2009-06-08
That error#15 is file not found. Boot up using livecd and log into your linux partition and go to /boot/grub. See if stage1 file is there.

---


---
title: "Can't find Ubuntu Partition - Wubi - Dual Boot Windows XP"
date: 2010-12-27
forum: Desktop Environments
---

### Post by ExpressNature on 2010-12-27
After update of Ubuntu 10.04, I got stuck with [COLOR=DarkRed]**grub rescue>**[/COLOR] screen. So I tried to list the partitions from live CD.

I executed as follows: >fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3888    31230328+   7  HPFS/NTFS
/dev/sda2            3889       11474    60934545    7  HPFS/NTFS[COLOR=DarkRed]**(where I partitioned some GB for Ubuntu)**[/COLOR]
/dev/sda3           11475       20023    68669842+   7  HPFS/NTFS

Disk /dev/dm-0: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table


There was no 'Ubuntu' partition in the above. It was needed to recover the grub 2.[B] 

Note: I used Wubi installer to install ubuntu 10.04 inside windows XP.

Please help to getback my windows XP atleast, as I dont have WindowsXP CD.[/B]

---

### Post by sikander3786 on 2010-12-27
See problem # 1 and later, Permanent Fix here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by ExpressNature on 2010-12-27
Thankyou :p

---


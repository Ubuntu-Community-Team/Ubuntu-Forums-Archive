---
title: "fat32 drive incompatible w/ WinXP setup/dual boot"
date: 2008-12-03
forum: General Help
---

### Post by aboutb on 2008-12-03
on Disk /dev/sdb: 37.0 GB:

I'm trying to dual boot on my extra 40gb internal hdd (it was previously formatted ext3), formatting as FAT32(or NTFS) with gparted doesn't allow windows setup to accept the harddrive, as I'm given the following error:

> Windows XP cannot recognize the partition you selected, delete the partition and select the unpartitioned space

(even though it shows in WXP setup that the drives format is FAT32 (or previously NTFS as formated by gparted as well))

if i do as asked, I'm given this error:

> The disk does not contain a Windows XP compatible partition, delete the partition and select the unpartitioned space

I've tried using hirens bootcd and the fdisk/partition utilities to format, but the same result

also, every time it's formatted, it's done in 15 seconds, I don't remember a drive being able to be formatted in that short period of time

> Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea04ea04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdd2fdd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x237a2780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20023   160834716    7  HPFS/NTFS


---

### Post by TeXtonyx on 2008-12-03
Maybe I didn't understand your post. Did you want to install XP
to a fat32 partition? If so, you will need to download a win98se
boot disk from [http://www.bootdisk.com/](http://www.bootdisk.com/) and from a floppy drive
type A:\sys C:  I think fdisk /s also works (/s) means system.

If XP recognizes fat32 boot files it may increase your chances.
I think XP usually installs to a fat32 partition, but if the
drive is unformatted doesn't offer you the chance of fat32.
Also do you have an upgrade XP install cd, or a clean install cd?
If you have an upgrade cd, putting the system files on the drive
may trick XP into installing, though it may look for a C:\Windows
If none of this is helpful, what you are looking for, sorry.

---

### Post by caljohnsmith on 2008-12-03
I think part of the problem you are experiencing might be because Windows does not like to be installed on a slave drive; it looks like you might have sdb as the slave drive of the sda drive. To install Windows to a slave drive, there needs to be a FAT/NTFS primary partition available on the master drive (sda) where Windows can stick its boot files. I would pull your drives out and put sdb in temporarily as the master drive, try to install Windows, and then you can revert back to your previous configuration if Windows installs successfully. How about giving that a shot and let me know if it works. :)

---


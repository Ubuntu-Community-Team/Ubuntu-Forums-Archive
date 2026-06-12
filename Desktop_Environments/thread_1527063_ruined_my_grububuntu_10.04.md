---
title: "ruined my grub/ubuntu 10.04"
date: 2010-07-08
forum: Desktop Environments
---

### Post by th1bill on 2010-07-08
I updated and rebooted. Not paying close enough attention I booted into my old HDD and updated again. Now I have a 314 gig file system that does not appear on my Boot Screen. I booted into the 40 gig that contains my old 10.04 and I did an Update Grub but to no avail. I can access the files of course, so it isn't the end of the world but I really want to et the new install on my new 320 gig back as my sd1 drive, any hope?

---

### Post by oldfred on 2010-07-09
If grub2 you should be able to reinstall from a liveCD or your old install.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you need more help on exact commands:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by th1bill on 2010-07-09
> **oldfred said:**
> If grub2 you should be able to reinstall from a liveCD or your old install.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you need more help on exact commands:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

[COLOR="DarkRed"]The problem with this solution is that, yes, I can always reinstall from the live CD but in doing so i loose all my virtual HDDs and the testing work I have going on and must begin, once more, from scratch.

Since this happened here is the info I have collected:

Here is the fdisk output:

root@th1bill-desktop:/home/th1bill# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000110bf

Device Boot Start End Blocks Id System
/dev/sda1 * 1 38162 306534400 83 Linux
/dev/sda2 38163 38914 6034433 5 Extended
/dev/sda5 38163 38914 6034432 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfb82fb82

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9327 74919096 83 Linux
/dev/sdb2 9328 9729 3229034+ 5 Extended
/dev/sdb5 9328 9729 3229033+ 82 Linux swap / Solaris

Disk /dev/sdc: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43954394

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 2396 19245838+ 83 Linux
/dev/sdc2 2397 5005 20956792+ 5 Extended
/dev/sdc5 2397 4891 20041056 83 Linux
/dev/sdc6 4892 5005 915673+ 82 Linux swap / Solaris

Disk /dev/sdd: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ecf4ece

Device Boot Start End Blocks Id System
/dev/sdd1 1 4974 39953623+ 8e Linux LVM
/dev/sdd2 4975 5005 248977 5 Extended
/dev/sdd5 4975 5005 248976 83 Linux

Disk /dev/sde: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d85a1

Device Boot Start End Blocks Id System
/dev/sde1 * 1 1024 3967969 c W95 FAT32 (LBA)[/COLOR]

---

### Post by oldfred on 2010-07-09
The boot info script gives a lot more info. Reinstalling grub is just the boot loader in the MBR. How would that change anything?

---

### Post by th1bill on 2010-07-09
[COLOR="DarkRed"]I tried the MBR method to no avail, maybe?

I booted back in to the old 10.04 and at the Terminal I tried once more to *update-grub* and when I rebooted there was my new install and everything in Bill's house is spun gold.  Thanks.[/COLOR]

---


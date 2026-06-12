---
title: "persis usb live- cannot access pen drive"
date: 2009-06-06
forum: General Help
---

### Post by ndcook on 2009-06-06
I have been looking for a solution for this for sometime. I have 2 partitions on a usb key. One is a windows fat32 and the second is a hidden ubuntu cd image. I'm running ubuntu live in persistent mode.

I followed the instructions from this website. 
[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive)

When I run the live usb I cannot access the usb drive at all. Do I need to edit my fstab?

my fdisk -l output is this. I need access to sdb1. gparted tells me it cannot find a mounting point?

Thanks


Disk /dev/sdb: 8032 MB, 8032092160 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         886     7116763+   c  W95 FAT32 (LBA)
/dev/sdb2             887         976      722925   1c  Hidden W95 FAT32 (LBA)
ubuntu@ubuntu:~$

/etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---


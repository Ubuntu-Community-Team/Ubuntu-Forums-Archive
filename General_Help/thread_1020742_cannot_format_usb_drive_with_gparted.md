---
title: "cannot format usb drive with gparted"
date: 2008-12-24
forum: General Help
---

### Post by freejimmy on 2008-12-24
hi ive read most of the forum talks regarding formating a usb drive.

and in all of those i came across the mentioning of gparted, great tool by the way! :P if it worked.

i always get the same error message after i try to format using fat32 [B]
An error occurred while applying the operations[/B] 

[B]GParted 0.3.8

Libparted 1.8.9

Format /dev/sdb1 as ext3  00:00:01    ( ERROR )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 248
end: 3944447
size: 3944200 (1.88 GiB)
set partitiontype on /dev/sdb1  00:00:01    ( ERROR )
libparted messages    ( INFO )
     	
Input/output error during write on /dev/sdb[/B]

has anyone encountered this problem???

---

### Post by jbrown96 on 2008-12-24
Not sure what the problem is specifically, but it might help to just blow the drive away. You can remove the partition table (Caution: you will lose all data) with the following command ```
sudo dd=if/dev/null of=/dev/sdb
``` You can stop this after a minute by pressing Crtl+c. Then try Gparted again. It will bring up an error and will want to create a new partition table; let it. If that is still causing problems, try creating it from the terminal. ```
sudo mkfs.vfat /dev/sdb
``` vfat is the "normal" flash drive partition type and will be compatible with Macs and Windows. You could change it to something else, but I wouldn't recommend it.

---

### Post by 2hot6ft2 on 2008-12-24
Make sure you unmount the drive before making partition changes or you'll have errors. If making more than 1 partition on the usb drive do it 1 partition at a time as it will remount after the first partition is created and you'll have errors, you have to unmount it again each time a partition is created.

---


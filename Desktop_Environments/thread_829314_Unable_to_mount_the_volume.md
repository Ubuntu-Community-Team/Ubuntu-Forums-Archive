---
title: "Unable to mount the volume"
date: 2008-06-14
forum: Desktop Environments
---

### Post by Naif.1 on 2008-06-14
Hello Guys,

I am having a problem accessing my hard drive from ubuntu. I am very new to ubuntu so be easy with me :). I have googled this problem but I did not find soulution :(


So, I have three partition on my laptop, C which has Windows vista, D which has all of my files, and E which has Ubuntu.

When I go to Computer and click on C or D, I can not acces these partition and it gives me this error:

Unable to mount the volume.


C and D file system is NTFS.


Please please help, I woild appreciate any help.


Thanks.

---

### Post by Naif.1 on 2008-06-14
up, please

---

### Post by tamoneya on 2008-06-14
can you go into terminal (applications->accessories -> terminal) and type:```
sudo fdisk -l
```Then post the output here.

Also please dont bump a post until at least 24 hours have passed.

---

### Post by Naif.1 on 2008-06-15
Thanks, here is what I got:


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020       10258    74212267+   6  FAT16
/dev/sda3           10259       14865    36999316    7  HPFS/NTFS
/dev/sda4           14866       19457    36885240    5  Extended
/dev/sda5           14866       19457    36885208+  83  Linux

```



Hope to find the solution. :)

---

### Post by tamoneya on 2008-06-15
from looking at that it appears that C: = /dev/sda3 and D: = /dev/sda2.  To mount them use the two following sets of commands.

C:
```
sudo mkdir /media/C_drive
sudo mount -t ntfs /dev/sda3 /media/C_drive
cd /media/C_drive
ls
```

D:
```
sudo mkdir /media/D_drive
sudo mount -t vfat /dev/sda2 /media/D_drive
cd /media/D_drive
ls
```

---


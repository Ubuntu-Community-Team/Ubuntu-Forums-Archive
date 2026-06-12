---
title: "Auto mount FAT32"
date: 2009-08-28
forum: Desktop Environments
---

### Post by override16 on 2009-08-28
Hi! :D
I have edited the fstab file to get ubuntu to auto mount my ACER (C: ) drive and my ACERDATA (D: ) drive. They mount OK, but I can't get read/write permissions on ACERDATA. The drives are FAT32. I found the following lines on a norwegian ubuntu forum, and the sda number is correct: 
```
/dev/sda2 /media/ACER vfat iocharset=utf8,rw,umask=000 0 0
/dev/sda3 /media/ACERDATA vfat iocharset=utf8,rw,umask=000 0 0
```
But still, I can't write to ACERDATA. Can someone check if the lines are correct? :confused:
Override16 :)

---

### Post by dumblebee100 on 2009-08-28
I dont know which thing is wrong in ur fstab but I got mine which works perfectly 

here is my fstab 
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=0dc610e4-ef43-49c0-9ac3-c319b9e49c76 /               ext4    relatime,errors=remount-ro 0       1
# /media/c was on /dev/sda1 during installation
LABEL=C         /media/c        vfat    defaults,umask=007,uid=1000,gid=1000 0       0
# /media/d was on /dev/sda5 during installation
LABEL=D         /media/d        vfat    defaults,umask=007,uid=1000,gid=1000 0       1
# /media/e was on /dev/sda6 during installation
LABEL=E         /media/e        vfat    defaults,umask=007,uid=1000,gid=1000 0       1
# /media/f was on /dev/sda7 during installation
LABEL=F         /media/f        vfat    defaults,umask=007,uid=1000,gid=1000 0       1
# none was on /dev/sda8 during installation
UUID=d45d8736-5850-44ef-a7b3-1e84e98df1dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

u can replace the labels by devices and u can get uid and gid from command
```
id
```

mine works nice so I think yours will also work good

---

### Post by override16 on 2009-08-29
the last 0 and 1, what does they mean? Should I have 0 0 or 0 1 in the end?

---

### Post by dumblebee100 on 2009-08-31
> **override16 said:**
> the last 0 and 1, what does they mean? Should I have 0 0 or 0 1 in the end?

as far as I know the last 1 means disk checking during the boot ..
if that is enabled the partition is checked for any inconsistencies due to bad sectors or any memory faults bcz of last power failure and things like that ...

did u ever did a fsck ..I mean filesystem check 

the last 1 means the exact same thing ..if u were already logged in ..you have to unmount partition and then do the fsck ...so doing fsck before the partitions even got mounted will be better idea ..so we do disk checking before mounting partition ie during the boot time ...so thats what reflected in fstab file 

I do kept 0 for my C partition bcz I know there are bad sectors and fsck cant remove them fully ..so I removed from disk checking sequence so that my ubuntu boots ...otherwise I will be stuck with fsck and it will never be completed ...my HDD is 5 years old ..so I have serious problems ...but u can disable it on all the drives if u wish ...but dont disable for ROOT partition ....bcz its needed ...just in case

---


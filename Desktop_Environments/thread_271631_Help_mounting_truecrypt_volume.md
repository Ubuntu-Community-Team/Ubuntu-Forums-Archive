---
title: "Help mounting truecrypt volume"
date: 2006-10-05
forum: Desktop Environments
---

### Post by drksun on 2006-10-05
$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris


My encrypted volume is /dev/hda2 its from a past windows install, i cant figgure out how to mount it..

$ sudo mount /dev/hda2 /media/hda2 -t ext2
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


$ sudo truecrypt /dev/hda2 /mnt
Enter password for '/dev/hda2':
Cannot read hidden volume header: Invalid argument

---

### Post by ctothej on 2007-05-08
bump

---

### Post by orb9220 on 2007-05-08
There is a gui for truecrypt called forcefield.
[http://bockcay.de/forcefield](http://bockcay.de/forcefield)

Works great

---


---
title: "New KDE install: where is FAT32 partition?"
date: 2007-03-18
forum: Desktop Environments
---

### Post by bg1256 on 2007-03-18
I just installed Kubuntu Edgy.  I've been using Gnome for about six months, and Gnome mounted the partition automatically, but in KDE, I can't seem to find it.

```
sudo fdisk -l
``` renders

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2           17144       17585     3550365   82  Linux swap / Solaris
/dev/sda3            5100       17143    96743430   83  Linux
/dev/sda4           17586       30401   102944520    b  W95 FAT32

Partition table entries are not in disk order


And

```
cat /etc/fstab
```

gives me

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a212c8af-dcb3-4def-a5e4-158cd76a25f6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3C384026383FDD98 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=45ED-B760  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=065bc9fa-bea9-4b65-8ad2-eab9d5ef5005 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


So, I'm not sure how I can access the FAT32 partition...

Any ideas? And I'm still pretty new to Linux, so the simpler the better :guitar:

---

### Post by MonkeyBoy on 2007-03-18
You could try Automatix 2.  Under misc. it has an automatic partition mounter.

---

### Post by bg1256 on 2007-03-18
I actually did try that, and it doesn't recognize my FAT32 partition.

I need to boot into Windows to see if it sees the drive. Perhaps it was corrupted during the new install.

---

### Post by airtonix on 2007-03-18
see this line : 

```
/dev/sda4           17586       30401   102944520    b  W95 FAT32
```

it is your fat32 partition

to mount it . type : 

sudo mount /dev/sda4

if that doesnt work for you then you might need to have somewhere for the disk to mount to (i take it you dont understand that a drive needs to have a folder in which to mount itself and display its contents? no offense)

create the folder for the drive : replace fat32 with a folder name you like...note this folder name becomes the name of the drive you will see on desktop.
```
sudo mkdir /media/fat32
```

then mount it : 
```
sudo mount /dev/sda4 /media/fat32 
```


hope this helps, if you get errors then you will probably need to provide extra arguments tot eh emount command...ie what filesystem type it is (ie vfat)...but im not exactly sure here so 

your next website to visit will be either of these : 
 Ubuntu Dapper : [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
 Ubuntu Edgey  : [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)


trust me ....lots of information

you can also get this info (alittle bit out of date) under your system help menu in your panel bar.

good luck compadre

---


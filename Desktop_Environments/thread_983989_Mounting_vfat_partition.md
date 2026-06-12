---
title: "Mounting vfat partition"
date: 2008-11-16
forum: Desktop Environments
---

### Post by pasha07 on 2008-11-16
Hey guys, 

I am new to Linux to go easy on me. I was trying to make Unison to work with my flash drive (the whole permission thing) and I added some extra lines under Volume tab --> mounting options (I think) of my sda4 partition (a vfat partition). Now, every time I try to mount the drive in Ubuntu by clicking on the icon, I get a message saying:

unable to mount to mount the volume. TODO: have to rethink extra options. 

here is my fstab (not sure if something gets changed there when you play around with the extra options)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0b7e3937-3a28-4ead-ae35-a50dad15b7e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=F08C-BB92  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=b6379461-263e-456d-9b0f-34e91577ce58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thank a bunch for the help. 

a

---

### Post by pasha07 on 2008-11-16
OK I corrected the problem by making a dir in /media and then manually mounting the partition to the same name 

sudo mount /dev/hda1 /media/59.6 -t ntfs -o umask=0222 

then going to properties, volume and deleting the lines added in the mount option under setting.

---


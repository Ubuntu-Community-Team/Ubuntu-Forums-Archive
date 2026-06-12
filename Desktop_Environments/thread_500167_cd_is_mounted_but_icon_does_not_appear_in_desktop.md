---
title: "cd is mounted but icon does not appear in desktop"
date: 2007-07-13
forum: Desktop Environments
---

### Post by mizar001 on 2007-07-13
Hi. 

I always had a cd icon appearing in the desktop when inserting a cd or dvd. But now this icon is no more shown and i have to manually umount the unit.

The other partitions and usb disks are correctly shown on the desktop. My fstab is :


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=fd6ee15d-88eb-4227-88db-e684e02e5710 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=00000000802F1F2E /media/winxp     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
#UUID=8818BF2718BF12E4 /media/public    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=461B-FCFA  /media/boh     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=15DD-435A  /media/oldgames     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=15E0-3D66  /media/datadisk2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=461A-0A4C  /media/datadisk     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=43240134-07ad-40d1-8772-cc0157aadb61 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,auto     0       0


What the problem can be ?

---

### Post by merlinus on 2007-07-13
Make sure that the box for volumes_visible is ticked in gconf-editor, apps, Nautilus, desktop.

-merlin

---

### Post by mizar001 on 2007-07-15
Yes. As i said other units and mounted usb devices are correctly shown on my desktop.

The only problem is for cd,dvd units.

---


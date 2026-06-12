---
title: "cant mount NTFS partitions on boot-up"
date: 2005-12-26
forum: General Help
---

### Post by ren wins on 2005-12-26
here's my fstab

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb6       /media/hdb6     ntfs    defaults        0       0
/dev/hdb7       /media/hdb7     ntfs    defaults        0       0
/dev/hdb8       /media/hdb8     vfat    defaults        0       0
/dev/hdb9       /media/hdb9     vfat    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/windows	ntfs	umask=0222	0	0
/dev/hdb6	/media/noise	ntfs	umask=0222	0	0
/dev/hdb7	/media/eyes	ntfs	umask=0222	0	0
/dev/hdb8	/media/static	vfat	umask=000	0	0
/dev/hdb9	/media/support	vfat	umask=000	0	0


i can access the fat partitions just fine, but i cant access hda1 hdb6 or hdb8
and i cant figure it out

---

### Post by MetalMusicAddict on 2005-12-26
Look [HERE]("http://ubuntuguide.org/#automountntfs").

---

### Post by ren wins on 2005-12-26
isnt that for ubuntu 5.04?

i'm using 5.05 and did it according to the help guide that's built into my version (at least i thought i did)

---

### Post by MetalMusicAddict on 2005-12-26
Doesnt matter with this. Works the same. ;)

---


---
title: "Where is mount / umount default option"
date: 2009-05-24
forum: General Help
---

### Post by sidewalkcynic on 2009-05-24
Before I re-installed Ubuntu 8.04 I triggered Gnome somehow to not mount my USB partitions when I inserted the media. And, I liked that, because I have 8 partitions on my USBs and I do not need to access all of them.

Now that I re-installed I don't have that option and it is difficult to manage all of the mounted partitions.

Anybody know how to toggle the default to umount?

---

### Post by Girl™ on 2009-05-24
Maybe you can edit */etc/fstab* to not auto-mount usb partitions?

---

### Post by kmitnick on 2009-05-24
yeah I guess it is the /etc/fstab

you need to add like this line
```
/dev/sdb   /media/usb_partition noauto,user,sync---etc 0 0 
```

---

### Post by sidewalkcynic on 2009-05-24
This didn't work, but I am going to try a restart```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=549a879e-1fab-4aae-9826-f6b1b1396a5a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=97951403-2316-4316-84d4-aea2cc70a366 /home           ext3    relatime        0       2
# /dev/sda3
UUID=be77acd3-9c41-4142-b2d6-8d4264efe064 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb       /media/usb_partition noauto,user,sync---etc 0 0
```

---

### Post by sidewalkcynic on 2009-05-24
Nope.

Didn't work on a restart either.

---

### Post by kmitnick on 2009-05-24
I  see that you just copied and pasted my post
first I need you to connect you USB device and run
```
sudo fdisk -l
```
post the output here

then you must create in /media and folder called usb_partition
and remove ---etc it is just noauto,user,sync

---

### Post by drs305 on 2009-05-24
Automounting *in general* is handled by gconf-editor. Open this for the automounting options:

```
gconf-editor /apps/nautilus/preferences/media_automount
```

It would also be possible to add the "noauto" option to the /system/storage/default_options/ section if they were all formatted the same and wanted to exclude one entire formatting type from automatically being mounted.

---

### Post by sidewalkcynic on 2009-05-25
gconf-editor did it thanks

---


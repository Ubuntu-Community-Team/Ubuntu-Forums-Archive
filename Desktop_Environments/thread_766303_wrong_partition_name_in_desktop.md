---
title: "wrong partition name in desktop"
date: 2008-04-25
forum: Desktop Environments
---

### Post by anomalous_underdog on 2008-04-25
I have a FAT32 partition mounted in /media/FILES. But in the desktop, as well as in Nautilus, its name appears as "phereData *"

I can't rename it in the right-click menu. How do I name it to FILES instead?

---

### Post by vanadium on 2008-04-25
A very good method to have USB drives mounted with a name you choose is to label them. How this is done depends on the file system. You can find the howto in each of the following links

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[http://www.debuntu.org/device-partition-labeling](http://www.debuntu.org/device-partition-labeling)

---

### Post by anomalous_underdog on 2008-04-25
sorry if I failed to mention it before but, the hard drive in question isn't a usb removable. its my primary master hard drive and the partition is in hda5. it always gets labeled as "phereData *"

---

### Post by anomalous_underdog on 2008-04-25
here's the contents of my fstab if it's any help

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/FILES    vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hda1       /media/WINOS    vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hdb1	/media/MORESPACE ntfs   defaults,utf8,umask=007,gid=46 0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---


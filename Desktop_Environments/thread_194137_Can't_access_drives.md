---
title: "Can't access drives"
date: 2006-06-11
forum: Desktop Environments
---

### Post by penguinchrissy on 2006-06-11
I'm trying to access my windows drives when I click on them I get a message
Unable to mount the selected volume.
error: device /dev/hdb1 is not removable

error: could not execute pmount

what do these mean and how do I fix them.

---

### Post by aysiu on 2006-06-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

### Post by taurus on 2006-06-11
You need to mount it before you can access it!!!  I assume it's NTFS filesystem so open a terminal (Applications -> Accessories -> Terminal), and type
```

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hdb1 /mnt/windows
sudo ls -la /mnt/windows

```

---

### Post by penguinchrissy on 2006-06-11
that seems to have worked taurus now I have this problem
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "windows".
I tried doing some sudo stuff but nothing I tried worked
Another thing how do I unmount

---

### Post by aysiu on 2006-06-11
```
sudo mount -t ntfs /dev/hdb1 /mnt/windows
``` mounts with read permission for root only. What you want is ```
sudo mount -t ntfs /dev/hdb1 /mnt/windows -o nls=utf8,umask=0222
``` To unmount it ```
sudo umount /mnt/windows
``` And if you want it permanently mounted, follow the instructions in the link I gave earlier.

---

### Post by penguinchrissy on 2006-06-11
It has worked but I'm finding that I can only mount 1 windows drive at a time do I need to change some of the numbers so I can mount another one or am I out of luck.

---

### Post by sarhento_lobo on 2006-06-11
You have to do it for each drive/partition that you want to access. Just be sure that you're giving the right parameters to the mount command, specifically the file system type (ntfs for ntfs, vfat for fat32).

---

### Post by penguinchrissy on 2006-06-11
I'm still having touble mount both of my drives when I do it they both mount but I can't access both I have to unmount one to access the other. My code looks like this they are both ntfs
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /windows ntfs nls=utf8,umask=0222 0 0

```
I'm sure both are right becuase when I do sudo mount -a the /dev/hdb1 /windows ntfs nls=utf8,umask=0222 0 0 works but then I do a sudo umount /windows then the second one works then I umount again and they are both unmounted

---


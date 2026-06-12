---
title: "Viewable Windows partition?"
date: 2005-12-12
forum: General Help
---

### Post by JSchwage on 2005-12-12
I was wondering, is it possible to be able to view a Windows partition in Ubuntu? I've tried other distros of Linux such as Mandrake and SuSe, and they have the capability to view a Windows partition. This is one thing I really miss and wish Ubuntu had. If there's any way to do this, please tell. :D

---

### Post by linrasta on 2005-12-12
Figure out what hd# it is and type mount hd# into the command line.  I think this works.  should be something like hdc or hdd, depending on how your hd is partitioned.

---

### Post by mcmuffy on 2005-12-12
You can view windows partitions by adding the following line to your /etc/fstab file

/dev/hda5	/media/windows ntfs	user,umask=0	0	0

This will automount the partition for you on boot.
Obviously you would have to swap hda5 with whatever drive your windows is installed to and you would need to make a windows folder in /media.

---

### Post by JSchwage on 2005-12-12
Alright, there's just one problem. I'm trying this on the Ubuntu Live CD. Any idea what the root password is set to be default?

---

### Post by RAOF on 2005-12-12
There is no root password.  At least, for the instal version.  Try "sudo <command>" instead.

---

### Post by aysiu on 2005-12-12
If you're using the live CD, you most likely want to mount /dev/hda1, but to be sure, you can run this command ```
sudo fdisk -l
``` If it's NTFS, try ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows
gksudo nautilus
```

---


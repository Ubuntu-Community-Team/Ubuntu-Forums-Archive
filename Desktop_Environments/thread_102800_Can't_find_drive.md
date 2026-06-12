---
title: "Can't find drive"
date: 2005-12-12
forum: Desktop Environments
---

### Post by saldie on 2005-12-12
Hi, I am trying to install a program and apt at one point tell me to insert the Breezy cd in the drive.
When I do, it does not see it.
I recently put in a new double layer dvd drive in and now i have a cd and dvd rive icon in "Computer".
Playing Cd's and Dvd's all work fine so how do fix this?

---

### Post by soulestream on 2005-12-12
your drive order probably changed.

post the output of your /etc/fstab

and ls -la /dev/cd*

soule

---

### Post by taurus on 2005-12-12
When you say it does not see your CD, what exactly was the error message?  Also, is the CD you downloaded and burned yourself or the one you received it for free?  Have you tried to mount it by hand to see if you can do that or not?

sudo mkdir /mnt/cdrom
sudo mount -t iso9660 /dev/hdc /mnt/cdrom

assuming that your CD drive is a /dev/hdc.  If not sure, look at the boot's message...

dmesg | more

---

### Post by saldie on 2005-12-12
Here is my fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Soule, don't now what the other file you asked for, sorry I am new to linux

Taurus, there is no error message, just keeps asking for it even though its mounted and I can access it.

---

### Post by saldie on 2005-12-13
Anybody elese have any ideas?
Thanks.

---


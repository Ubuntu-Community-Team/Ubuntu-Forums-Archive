---
title: "[SOLVED] USB automounting problem"
date: 2008-12-12
forum: Desktop Environments
---

### Post by Azyl on 2008-12-12
hy i have a problem i can`t mount usb drives automaticly, when i insert them nothing hapens, if i try in nautilius to double click the usb drive or rigth click & mount it gives an eror can`t mount file

my fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
ffff8ec2-15d5-4d9a-ba96-ecca9527c7a4 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda5	 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/usb   	auto 	user,noauto,exec		0	0

i can mount usb drive only by using the terminal with the mount command but even then there is a problem even if i use the mount command as a user only a part of the folder on my usb drive have permision setings for writing & modifing files

the problem is that i want usb drives to automount when i plug them in the usb because is dificult for my parents or sister to use usb drives

strangely the cdrom works fine.

is there another config file that i should modify or is there an option for the fstab? what shoul i do?

---

### Post by joshua1983 on 2008-12-15
Hi, I have a similar problem, but I can mount USB disk less than 4Gb ... a 4Gb usb key I must mount manually using mount :confused:
I think should be a gub, and someplace I read the bug...

---

### Post by louistan3 on 2008-12-15
If i remember correctly, there's something with automounting in the gconf-editor.

sorry, im not home right now so i cant check.

Il try to get back here if i find anything.

---

### Post by Azyl on 2008-12-23
i managed to make it work the problem was the /etc/fstab file it had an eror in the syntax now it mounts them, and i changed the type of the usb drive from auto to vfat.

---


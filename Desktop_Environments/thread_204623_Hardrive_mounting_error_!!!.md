---
title: "Hardrive mounting error !!!"
date: 2006-06-27
forum: Desktop Environments
---

### Post by tuxy on 2006-06-27
I can't see my hardrive icon on my Ubuntu Dapper desktop which used to be there before. I stuffed up the Grub menu when I installed Windows on it and now I have reinstalled Grub through Knoppix live CD and now I cant boot Windows(but I can boot Ubuntu) and I cant see my HD on my Ubuntu desktop.

This is what I get when I type in:
/etc$ cat /etc/fstab
cat: /etc: Is a directory
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hdb2 is the place where my Ubuntu is installed. I can see "errors" in the above hdb2 section. How to fix this error and regain the hard disk on teh desktop ?

I have installed Grub by making a 'temp' directory and mounting the hdb2 in the 'temp' directory and then changed the root through 'chroot' to the temp folder and then 'grub-install hda'.

---

### Post by Ramses de Norre on 2006-06-27
The errors thing in fstab is an option to define what to do when errors occur (in your case remounting the volume read-only) so it is certainly no indication that there are errors ;)
And what do you mean by I can't see the hd? Ubuntu is installed on it and you can boot ubuntu? I guess the partition works then..

---

### Post by tuxy on 2006-06-28
Sorry I was mistaken then! Basically what I want is my hda1 icon on the desktop is missing and it is not auto mounted when I boot into Ubuntu.

---


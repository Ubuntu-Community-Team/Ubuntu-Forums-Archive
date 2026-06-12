---
title: "[B]Getting a Second HD To mount in Ubuntu[/B]"
date: 2005-05-25
forum: Desktop Environments
---

### Post by bryantyse on 2005-05-25
Hello all,

I am new to Linux myself and have a second HD that the computer can see, but will not auto mount.  What is the best way to get this drive to auto mount when the computer boots?  Is there a utility for me to use or do I need to go into /etc/fstab and manually configure it?

Thanx,

BT
**Getting a Second HD To mount in Ubuntu**

---

### Post by jasmuz on 2005-05-25
[QUOTE=bryantyse]Hello all,

I am new to Linux myself and have a second HD that the computer can see, but will not auto mount.  What is the best way to get this drive to auto mount when the computer boots?  Is there a utility for me to use or do I need to go into /etc/fstab and manually configure it?

Thanx,

BT
**Getting a Second HD To mount in Ubuntu**[/QUOTE]
 My best recomendation is for you to edit the /etc/fstab, like this

#sudo gedit /etc/fstab

Here is a copy of mine:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/Windows  ntfs    umask=0222      0       0

the /dev/hd* refers to the disk as linux sees it
the /media/* refers to the place it will mount
the type is the filesystem (you can read but not write into NTFS)
the options....it depends on what atributes you want
dump...got no clue what it does
pass...error verification on every mount (takes time)

---

### Post by jkndrkn on 2005-05-25
Editing fstab will be the most direct route.

---


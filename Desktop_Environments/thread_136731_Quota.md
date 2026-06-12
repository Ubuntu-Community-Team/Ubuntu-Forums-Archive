---
title: "Quota"
date: 2006-02-26
forum: Desktop Environments
---

### Post by startx on 2006-02-26
I have installed quota and am trying to edit my /etc/fstab to reflect userquota for /home . As you can see from my fstab, my drive information has /dev/hda1 as one big mount point and /dev/hda5 as my swap file. 

[HTML]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1     /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/sda1     vfat iocharset=utf8,umask=000   0        0
/dev/sda2       /media/sda2     vfat iocharset=utf8,umask=000   0        0
[/HTML]

My goal is to to edit fstab for user quota. Can I have two lines pointing to hda1? Will this edit do the trick?
/dev/hda1     /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1     /home        ext3    defaults,usrquota              0       2

What is my best avenue of approach? I have cold feet after so many hours of configuring the file system and samba install and I would feel better if some body else took a look at this. Thanks!

---


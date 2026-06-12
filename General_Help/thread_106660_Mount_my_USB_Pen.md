---
title: "Mount my USB Pen"
date: 2005-12-21
forum: General Help
---

### Post by ace2005 on 2005-12-21
When i try to follow a link i created to teh device i get this:

> Could not mount device.
The reported error was:
mount: only root can mount /dev/sda1 on /mnt/pen

I have to go to the link with "sudo konqueror" and then mount it, go there and then i can access the files. I want my regular user to have access to those files, to be able to delete and moce them.

My /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /mnt/.winxp     vfat    defaults        0       0
/dev/sda1       /mnt/pen        vfat    defaults        0       0
/dev/hdb1       /mnt/archive    reiserfs defaults        0       2
/dev/hdb5       /mnt/work       vfat    defaults        0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

---

### Post by briancurtin on 2005-12-21
add yourself to the proper group with root privilages. the first username you created should be a part of that group, but if not, you can add those privilages.

---

### Post by ace2005 on 2005-12-21
If i can mount and unmount cds ther has to be a way to mount and unmount this

i'll try "user,noauto"

I don't want to give myself root access and this is the first and only account made

---

### Post by ace2005 on 2005-12-21
Oh that works fine :D

---


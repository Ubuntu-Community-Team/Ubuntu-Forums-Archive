---
title: "mount local filesystems on boot"
date: 2006-01-15
forum: General Help
---

### Post by eyebrowman92 on 2006-01-15
everytime i boot, on the splash screen, the mounting of local filesystems fails. i do have a dual boot set up with windows. does anyone know what the problem is or how to fix it?

---

### Post by jasmuz on 2006-01-15
Check your /etc/fstab to see if erverything is in order.

---

### Post by eyebrowman92 on 2006-01-15
what do you mean?

---

### Post by eyebrowman92 on 2006-01-15
i get this

```
@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     nfts    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Omnios on 2006-01-15
[QUOTE=eyebrowman92]i get this

```
@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     nfts    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```[/QUOTE]

 Is it hda1 you are having problems with. as you have it set up hda1 needs a directory called hda1 in .media/ what you have is media/hda1 so you will need a file in media called hda1 to mount to it.

  You can make a file called anything you want and mount to it by making a directory called the same name in media. Id advise windblows lol.

---

### Post by eyebrowman92 on 2006-01-15
haha thanks but i still dont understand what you're saying..?

---

### Post by dcstar on 2006-01-15
[QUOTE=eyebrowman92]haha thanks but i still dont understand what you're saying..?[/QUOTE]
Every "Mount Point" must exist as a Directory - if it doesn't then there is nothing for Linux to "attach" the filesystem to.

---


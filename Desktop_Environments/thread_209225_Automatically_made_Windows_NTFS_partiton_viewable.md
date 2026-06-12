---
title: "Automatically made Windows NTFS partiton viewable"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Athanasius on 2006-07-04
I am dual-booting and for some reason my windows partition was automatically put on the desktop and I can open files from it.  How in the world did that happen?  I am happy that it did happen but I don't know how it happened.  In my fstab file it says the following:
>   
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


It also says that there is some sort of an error with the hard drive when I boot into ubuntu and I imagint that is what it is talking about.  Can anyone shed some light on the situation so that I don't get that error anymore?

---

### Post by reacocard on 2006-07-04
ubuntu automatically enables all partitions by default. the line in your fstab that does it is
```
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
just comment out (add a # to the start) that line and your windows partition will no longer mount automatically. for the error, it would be helpful to know what it says.

---

### Post by GTvulse on 2006-07-04
[QUOTE=reacocard]ubuntu automatically enables all partitions by default. the line in your fstab that does it is
```
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
just comment out (add a # to the start) that line and your windows partition will no longer mount automatically. for the error, it would be helpful to know what it says.[/QUOTE]
Better yet, add ```
user,noauto
``` to the options string, instead of simply commenting out the line. You will be able to mount and unmount the windows partition manually whenever you need to access it.

---

### Post by Athanasius on 2006-07-04
Thank you for the information.  Does anybody know why I am getting an error message?

---

### Post by dmizer on 2006-07-04
[QUOTE=Athanasius]Thank you for the information.  Does anybody know why I am getting an error message?[/QUOTE]
no way of knowing that until we know what exactly the error message is.

---


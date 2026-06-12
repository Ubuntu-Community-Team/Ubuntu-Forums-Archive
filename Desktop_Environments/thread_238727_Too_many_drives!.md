---
title: "Too many drives!"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Aulden on 2006-08-18
Hi All, 

Got a computer with a large drive. I've split it up a few times (originally to install windows along side but haven't had a need to... YAY) and when I open the computer window I have a whole HEAP of drives and cdroms. I have 1 dvd writter but now it has 3 showing in this window:confused: . And each drive is there at least once but sometimes twice. 

How or where do I configure this window and what to show? 
I would like it to show just the filesystem, home (it's on a seperate drive), and 1 dvd. (possibly one other drive). How to do this?

One other bonus would be having the dvdrom and flash drive appear on the desktop when mounted. I know this can be turned on in configuration editor but I don't want all the drives on the desktop... 

It's all a mess... I want bring this chaos to order!](*,) 
Any help?!

Thanks, 

Aulden

---

### Post by hopstah on 2006-08-18
post the contents of your /etc/fstab file here

---

### Post by Aulden on 2006-08-18
It is as follows:
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               reiserfs notail          0       1
/dev/sda7       /home           reiserfs defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda8       /media/sda8     reiserfs defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Again I only need the sda7(Home) sda5(root) showing with the floppy and DVD. (And not 3 DVD Roms... )

Also how to name these drives? (e.g for sda1 to be WindowsC or something if needed someday) I know this can be aranged when installing Ubuntu.

Thanks!!!!

---

### Post by latebeat on 2006-08-18
I can't help you with the other problem as your fstab seems fine. However regarding this:
> **Aulden said:**
> 

Also how to name these drives? (e.g for sda1 to be WindowsC or something if needed someday) I know this can be aranged when installing Ubuntu.

Thanks!!!!


open a terminal and create a folder for the drive you want. For example for windows do: 

```
sudo mkdir /media/WindowsXP
```

and then change the entry in the fstab:
```
/dev/sda1 /media/WindowsXP vfat defaults,utf8,umask=007,gid=46 0 1
```
note that if you want write permissions as well you must add instead:
```
/dev/sda1 /media/WindowsXP vfat defaults,utf8,umask=027,gid=1000,uid=1000 0 1
```

assuming your id is 1000. Type 'id' to find out.

---

### Post by Aulden on 2006-08-21
Thanks a heap for that. 

It will help to obtain some order... But today I have FOUR DVDRoms... 4!!!

Hope soneone can help!

Thanks all,

---


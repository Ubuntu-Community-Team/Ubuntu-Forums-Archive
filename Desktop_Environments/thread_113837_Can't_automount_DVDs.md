---
title: "Can't automount DVDs"
date: 2006-01-07
forum: Desktop Environments
---

### Post by ijanos on 2006-01-07
I'm upgraded my Ubuntu 5.10 to Kubuntu using apt-get install kubuntu-desktop then upgraded it to KDE 3.5. Now everything works fine except the automount of DVDs. The automount works in other cases like plug in an USB pendrive or place a CD in my drive. But when I'm put a DVD in the same drive a konqueror window comes up with the follwing text:
> An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.
The disk remains unmounted. But I can mount it from command line as root so I think the KDE mess up something, but don't know what.
While I used gnome, everything worked fine with the same disks and drive.
My fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda4       /media/hda4     vfat    utf8,uid=1000,gid=1000        0       0
/dev/hda3       none            swap    sw              0       0
/dev/cdrom      /media/cdrom0   udf,iso9660 user,noauto     0       0


PS: I googled up the error message and searched the forum but i can't find anybody who has the same situation with only the DVD disks.

---

### Post by nikkkko on 2006-04-09
> i can't find anybody who has the same situation with only the DVD disks.
I too have this problem, but only if the DVD is write protected.  (I don't know how to fix it, but at least you're not alone).

---


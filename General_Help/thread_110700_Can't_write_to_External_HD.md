---
title: "Can't write to External HD?"
date: 2005-12-31
forum: General Help
---

### Post by Nightmare JG on 2005-12-31
Hi, i'm a bit of a newb in this case.
I have an external HD (/media/sda5) mounted at /dev/sda5.
My problem is that it seems only root can write files to this disk.
I tried sudo chmod 777 /dev/sda5 and sudo chown myusername.
Niether worked.
I NEED total acsess to this drvie, ll my files, including my website, are on this drive.
It's fat32 by the way.

Thanks,
Jacy Gaddis

---

### Post by tonym on 2005-12-31
Have you tried chmod 777 /media/sda5 ?

---

### Post by Norberg on 2005-12-31
Run "sudo nautilus" then you run the filemanager whit root-acess so you will be able to write to all directories.

---

### Post by earobinson on 2005-12-31
[QUOTE=Norberg]Run "sudo nautilus" then you run the filemanager whit root-acess so you will be able to write to all directories.[/QUOTE]
That is only a workaround

can you post your fstab? I assume you edited it?

---

### Post by Nightmare JG on 2006-01-01
Sure, but I haven't really messed with it much. Not sure what all that means.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     vfat    defaults,user        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---


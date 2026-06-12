---
title: "cd burned in k3b"
date: 2005-12-21
forum: Desktop Environments
---

### Post by Strannik on 2005-12-21
I just burned a cd in k3b it said it was completed successfuly. It ejected the cd. Then I insterted it and was surprized that it didn't mount automatically. tried to mount it:
```
mount /dev/hdd
``` but got the following:mount: No medium found.
Then i tried to do it like this: ```
sudo mount -t iso9660 /dev/hdd /media/cdrom0
```, same error: no medium found. then i rebooted into windows and i could see my cd with the stuff that i burned on it and was able to read it without any problems. Could somebody tell me why this is happening?:confused:

---

### Post by aysiu on 2005-12-21
Do other CDs automount?
Do other devices (USB drives, for example)?
What's the output of this command? ```
cat /etc/fstab
```

---

### Post by Strannik on 2005-12-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     vfat    iocharset=utf8        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

other cd's mount ok. only this one. usb stuff i mount manually (like it more that way...for some reason, i just like to use the terminal)

---

### Post by dcstar on 2005-12-21
[QUOTE=Strannik]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     vfat    iocharset=utf8        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

other cd's mount ok. only this one. usb stuff i mount manually (like it more that way...for some reason, i just like to use the terminal)[/QUOTE]
I had lots of problems with the Nautilus/Gnome automounter, I installed pmount and things improved, it may be worth trying.

---


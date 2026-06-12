---
title: "weird popup at mounting a cd"
date: 2008-08-22
forum: Desktop Environments
---

### Post by amarantus on 2008-08-22
at some point of working with a newly installed xubuntu (8.04.1) an irritating thing came up. When I insert a cd into the drive, it is automatically mounted and the icon appears on the desktop (not in thunar though), however a popup shows up saying that the drive cannot be mounted:
```

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.
```
Then, after clicking OK I can normally work with the CD - namely read its contents. It is very irritating though, especially for the other users of the computer (my family - almost totally convinced to Ubuntu:guitar:)

Pressing the button on the drive, unmounts the cd and ejects the cd tray... however another popup window shows saying:
```

umount: /dev/scd0: not mounted
umount: /dev/scd0: not mounted
eject: unmount of `/media/cdrom0' failed.
```

Could anybody help with this tiny, but annoying problem?
Here's my fstab:# /etc/fstab: static file system information.
```

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0811556b-f33c-4056-a5c1-838cc67ce2b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b03fe2e4-276a-43d0-a510-d42c1ba14fda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=AE84BE4E84BE18B3 /mnt/dysk_c ntfs-3g defaults,locale=pl_PL.UTF-8,ro 0 1
UUID=68CCF46CCCF435C2 /mnt/dysk_d ntfs-3g defaults,locale=pl_PL.UTF-8,ro 0 1
```
Thanks for help in advance.

---

### Post by mcduck on 2008-08-22
AHve you tried ejecting the CD from Linux, instead of pushing the drive button?

It could be that pushing the drive button dioesn't unmount the disk properly, and that's what's casuing the error messages you see.. (mtab shows that the drive is already mounted, because it wasn't correctly unmounted the last time).

---

### Post by amarantus on 2008-08-23
I can add to my first post that when i mount a device that is writable (USB stick) i get TWO thunar windows popping out with the content. It suggests there are 2 parallel auto-mounting processes. 

Anyone please?

---

### Post by peppe1234 on 2008-08-29
Can I just say that I have the EXACT same problems as you do.
I use Xubuntu.
If I find a solution I'll post it here, and if you've already solved it, please tell me how you did it :)

---

### Post by fchristophersen on 2008-09-19
i had the exact same problem in xubuntu 8.04. the only way i found to solve it, is going to xfce settings -> file manager -> advance -> configure -> and unchecking "mount removable drives when hot plugged", "mount removable media when inserted" and "browse removable media when inserted"
the error message doesnt popup anymore. but the downside is that thunar doesnt automatically open CDs or pendrives. you will have to double click on their desktop icon to open them. hope it works for you...

---

### Post by xjgnsdof on 2008-10-05
I get the same problem (though it's more of an inconvenience): when I pop in a CD or USB drive, two windows pop up to show me the contents of the medium. I'll be tracking this thread for answers and reporting back if I find anything on my own.

---

### Post by petr.simacek on 2008-11-24
I have the same problem in Xubuntu 8.10 Intrepid Ibex. P.

---


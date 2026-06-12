---
title: "need to copy file to floppy"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Waymo on 2005-11-21
hi all,
im having a problem. here it is.
i am running the latest ubuntu distro at home, i created a file on the /home/damienb/ directory. tried to copy off here to floppy yesterday but couldnt (think the drive itself was faulty)

so i thought id take the hd out and install it in a newer machine and see if i could copy it off here. but now im stuck in a terminal only display and i cannot seem to copy the file. ive check the net for some answers,,,but still cannot get the file to copy.

i tired this
mount -o rw /dev/fd0 /media/floppy0
and got the error "you must specifiy the file system type"

any ideas greatly appreaciated
Damien

---

### Post by tedius on 2005-11-21
You need to add a file system type to your mount command.
Try this instead:

mount -t vfat /dev/fd0 /media/floppy0

or if that doesn't work use "auto" instead of vfat.

FYI:
Mount needs to know the file system type that it will be mounting as well as   the device and mount point.

vfat is the FAT32 system used by windows, and is what is used for most Floppies and USB devices (purely because every thing can read it)

auto will try its best to guess what file system it is you are trying to mount.  I have never had any problems using auto, but I find it neater to use the correct tag.

Hope this helps :D

---

### Post by Waymo on 2005-11-21
Hi 
that worked perfectly, and got me out of a jam!
cheers!

Damien

---


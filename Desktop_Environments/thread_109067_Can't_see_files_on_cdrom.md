---
title: "Can't see files on cdrom"
date: 2005-12-27
forum: Desktop Environments
---

### Post by ryan76 on 2005-12-27
Hi, I'm not sure what I did but now the CDROM comes up as having nothing on it when I know it does.

Yesterday I was trying to install firefox 32-bit on AMD64, I uninstalled everything but no go. Also I was playing with Bastille but I put it back to the defaults so that shouldn't affect anything.

When I open a File Browser it lists cdrom0 but can't see the files.

Any help greatly appreciated
Thanks

---

### Post by amohanty on 2005-12-27
So just to be clear, when you insert a cd in the drive, does the cdrom icon show up on your desktop?

AM

---

### Post by ryan76 on 2005-12-27
No, it did when I did a fresh install of Breezy a couple of days ago but now it doesn't.

---

### Post by amohanty on 2005-12-27
Is it (cdrom) listed in your /etc/fstab?
Better yet, if possible post your /etc/fstab.

AM

---

### Post by ryan76 on 2005-12-27
Cheers for the help

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by amohanty on 2005-12-27
Try changing this line to:

> /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

to 
> /dev/hdc        /media/cdrom0   auto  user,noauto     0       0

Also in System->Preferences->Removable drive and Media Preferences in the Storage tab make sure the first three options are checked.

HTH
AM

---


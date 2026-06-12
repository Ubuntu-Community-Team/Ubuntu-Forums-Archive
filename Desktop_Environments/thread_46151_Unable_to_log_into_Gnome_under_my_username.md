---
title: "Unable to log into Gnome under my username"
date: 2005-07-03
forum: Desktop Environments
---

### Post by LazyIvan on 2005-07-03
Hi,

Currently, I am unable to log into Gnome on my main username on my Ubuntu 5.04.  It merely removes the graphics of the login screen so it is the background for about 15 seconds, and then screen blacks out and it returns to the login screen.  This all happens before the Ubuntu frame appears, so I am led to believe it is a problem with gnome.  I have tried removing the .config files/folder and also modifying the home directory, and am unsure of what to try next to fix this problem.

Any help would be greatly appreciated.

---

### Post by Morimando on 2005-07-03
some more info please... like errors.
Check if your home folder is read/write, if it's a FAT32 it could also have problems with permissions. check if in "fstab" /home partition has "defaults" in it.

---

### Post by LazyIvan on 2005-07-03
Where can you see the error messages at?

My home folder is chmod 755 so I think thats fine.  There are some defaults in my fstab, here is the output:

more /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3      /media/windows  ntfs    umask=0222      0       0
/dev/sdb2      /media/ipod  vfat    rw,user,noauto,noatime,shortname=winnt 0 0

---

### Post by jlacroix on 2005-07-03
I have this problem quite a bit.

Make certain you deleted all the hidden files, ESPECIALLY .gconf.

then, login under failsafe terminal.

Issue the commands:

sudo chown your_user_name -R /home/your_user_name

Then:

sudo chmod 0666 /home/your_user_name/*

Log out by typing "exit" then log into Gnome.

If it works so far, you will get a partial desktop and at least two error messages.
If that is the case, alt+ctrl+backspace, then do a full reboot.

At that point, all should be well.

---

### Post by LazyIvan on 2005-07-03
That fixed it right up, thanks a ton, jlacroix

---


---
title: "Installing .deb packages"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Steve Croteau on 2006-01-05
Greetings Ubuntu!
I'm a recent convert from Fedora and have what should be a easy question for you.  I've discovered that I need to update the "pmount" package so my floppy drive will function on my Dell Inspiron 2650 laptop.  I have the updated package and can't figure out how to install the darn thing.  Don't laugh too hard now. :oops:

Any help is greatly appreciated.  Thank you, Steve

---

### Post by Imexius on 2006-01-05
sudo dpkg -i <filenamegoeshere>

---

### Post by Steve Croteau on 2006-01-05
Thank you, the install was easy.  However, after rebooting then attempting to access the drive I receive the following error:

Warning: device /dev/fd0 is already handled by /etc/fstab,
supplied label is ignored
mount:  I could not determine the filesystem type, and none was specified
Error: could not execute pmount


**/etc/fstab as follows**:

proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


**Thank you again!!!**
Steve

---

### Post by Sef on 2006-01-05
This is what I posted on another thread.  I followed the directions and my floppy works just fine now.  

You might want to uninstall the package you installed yesterday.

> There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

I found that bug and fix from this thread: [http://ubuntuforums.org/showthread.php?t=93139&page=2](http://ubuntuforums.org/showthread.php?t=93139&page=2)

---

### Post by Steve Croteau on 2006-01-06
Thank you,
The process you just outlined is exactly what I previously did.  I repeated the process again but still got the same error message(s) posted above.  I'm still at a loss to acheive floppy drive functionality although I did hear the drive being accessed prior to the errors.

Steve

UPDATE: Deleting the "/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0" line from /etc/fstab solved the drive mounting problem.

---


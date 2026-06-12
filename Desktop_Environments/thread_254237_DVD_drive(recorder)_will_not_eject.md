---
title: "DVD drive(recorder) will not eject"
date: 2006-09-09
forum: Desktop Environments
---

### Post by gu014 on 2006-09-09
Hello,
My dvd drive will not eject after pressing the eject button.  I rebooted the system with the same result.  If it helps here is the contents of my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0


Any help would be greatly appreciated as i do not know where to go from here.  Thank you.

---

### Post by kidders on 2006-09-09
Linux often locks optical drives while they are in use. Perhaps this is the problem.

Try typing "eject" into a terminal window ... or "eject /dev/hdb" (or hda), since you seem to have more than one drive. It's possible that you'll get an error message suggesting the filesystem is busy, in which case, you should make sure you're not using any files on your DVD and try again.

Any help?

**Edit:** The handiest way for find out if files are open someplace is with something like **lsof | grep /media/cdrom0**

---

### Post by gu014 on 2006-09-09
Thank you for your reply,
I tried your suggestions with no luck.  the eject for the drive in question just hung for a couple minutes, provided no error messages, and returned to the console prompt.  the eject command worked for my other dvd drive(rom drive).  

Would you happen to have any other suggestions as this is truely worrying me to death. :(

---

### Post by orb9220 on 2006-09-09
Does it happen on all disks? specific disks?

I have two dvd drives but only one fstab entry Have you been adding fstab entries. You do not need two fstab entries for two drives.
Mine is:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
and works for both of my drives.

---

### Post by gu014 on 2006-09-09
well, it has never happened before.  i was in the process of backing up a dvd disk.  the task completed but i have been unable to eject the disk ever since.
I suppose i will edit the fstab file and see what happens?

---

### Post by gu014 on 2006-09-09
well, i tried it with just the one entry in /etc/fstab and it yields the same result.... any other ideas?

---

### Post by kidders on 2006-09-09
Editing your /etc/fstab probably won't have much impact ... orb9220 seems to be managing one of his drives statically with /etc/fstab and leaving the other one up to his hal/dbus/etc. for some reason. The single /etc/fstab entry doesn't apply to both of his drives.

I suppose one thing worth trying is to try to eject the disc while your machine is rebooting. If that doesn't work, you'll have to poke it with a paperclip (ie it's physically jammed).

---

### Post by bukwirm on 2006-09-09
Try mounting, then unmounting the drive.

---


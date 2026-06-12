---
title: "can not see the ntfs disks"
date: 2005-11-12
forum: Desktop Environments
---

### Post by senzacionale on 2005-11-12
when i click on hda1 or hdb1 in desktop i get this message!

the folder content cold not be displayed.
You don't have the permissions necessary to view the content of "hda1"

What i must add in /etc/fstab that i can see this disk

---

### Post by NeoChaosX on 2005-11-12
What's in your /etc/fstab right now?

---

### Post by PenguinZdravko on 2005-11-12
I had the same problem. In your /etc/fstab, in the line of ntfs partition replace "defaults" with "ro, umask=0222" (without the "'s).

---

### Post by senzacionale on 2005-11-12
fstab is like this now. I change defaults with ro, umask=0222 but i still get the message that i don't have permissions for hda1


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults            0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    ro, umask=0222     0       0
/dev/hdb5       /media/hdb5     ntfs    ro, umask=0222     0       0
/dev/hdb6       none            swap    sw                  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0

---

### Post by senzacionale on 2005-11-12
i fixed the problem.Fstab is now like this

ro, user, umask=0222

is ok this, it works but i don't know if is ok!

---

### Post by NeoChaosX on 2005-11-12
First off, remove those spaces so the line reads "ro,umask=0222". A space after the comma will confuse the mounting program.

Secondly, did you try going directly to the /media/hda1 folder and browsing it from there? You could try remounting everything with a **sudo mount -a** in the console and see if that works.

---


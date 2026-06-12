---
title: "Can't access my other hardrives. (Solved)"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Rackerz on 2005-11-16
Im trying to play some music which is on another drive but Kubuntu keeps telling me it can't access the drive even though it is mounted.

---

### Post by aysiu on 2005-11-16
Are these Windows drives?

---

### Post by Rackerz on 2005-11-16
Yes, both are NTFS. I can access them through the root user but not under my super-user account. Im guessing it's got something to do with permissions.

Rackerz

---

### Post by lutrafobic on 2005-11-16
Are you mounting them manually (with mount -t ntfs....) 
or in you /etc/fstab? (auto-mount-boot-thingy)

---

### Post by Rackerz on 2005-11-16
I'm just trying to access them, just clicking them and trying to use them.

---

### Post by lutrafobic on 2005-11-16
Yes, i got that, but the reason why you can't access them has to do with rights and to solve the problem once and for all, you need to configure the /etc/fstab correct.
(or else you have to read the files with higher permissions then your regular username everytime you need to access the files)

the quick solution is to just start the file-browser with sudo but that would be annoying in the long run.

Permanent solution: -configure /etc/fstab
Quick solution: sudo konqueror (in terminal)

If you want the permanet solution, get back with information about which drive (eg /dev/hda)it is and where the mounting point is. (eg. mnt/windows_drive)

---

### Post by Rackerz on 2005-11-16
Here is what i got from /etc/fstab,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdd1       /media/hdd1     ntfs    defaults        0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Is that what you wanted? Sorry if its not I'm a bit of a noob lol.

Thanks :)

---

### Post by lutrafobic on 2005-11-16
[QUOTE=Rackerz]Here is what i got from /etc/fstab,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdd1       /media/hdd1     ntfs    defaults        0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Is that what you wanted? Sorry if its not I'm a bit of a noob lol.

Thanks :)[/QUOTE]


That's what I needed, if you want right to access the drivers that are for Windows you need to add "umask=0222" on the lines regarding the NTFS drives. Like this:

/dev/hda1            /media/hda1          ntfs         umask=0222             0            0
/dev/hdd1            /media/hdd1          ntfs         umask=0222             0            0

and for these changes to take effect you have to reboot.
When rebooted you should have full reading rights of the files.

---

### Post by aysiu on 2005-11-16
Follow these directions:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Except when you're instructed to ```
sudo gedit
``` type ```
sudo kwrite
``` instead.

---

### Post by Rackerz on 2005-11-16
Thanks guys! Worked a charm ;)

---


---
title: "Partition permision"
date: 2005-09-21
forum: Desktop Environments
---

### Post by erhard on 2005-09-21
Hey guys. I have a FAT32 partion where i store my data in both Windows and Linux. I can paste data onto the drive with no peoblems at all.

The thing is however i can't get amule to use on of my folders on the FAT32 partition as the "complete" folder. Everytime i try that amule shows up a window that say's something about not having permission or something like that.

Would anyone happen to know how to solve that problem?

Thanks in advance.

---

### Post by aysiu on 2005-09-21
What does your /etc/fstab look like?

---

### Post by erhard on 2005-09-22
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows1  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb       /media/windows  vfat    iocharset=utf8,umask=000   0       0
#Added by winmac_fstab utility
/dev/hdb1 /media/9\040GB\040Disk\040(hdb1) vfat umask=0002,gid=109 0 0

---

### Post by aysiu on 2005-09-22
[QUOTE=erhard]
/dev/hdb       /media/windows  vfat    iocharset=utf8,umask=000   0       0[/quote] Well, this one has the right permissions.

> 
/dev/hdb1 /media/9\040GB\040Disk\040(hdb1) vfat umask=0002,gid=109 0 0 I'm not sure about this one, though.

Are you using hdb or hdb1 for your aMule stuff?
Also, I went to the aMule page, and it said "New features include SecureIdent (SUI) support, **complete FAT32 support**, full aMuleWeb and CAS (including wx GUIs)...." So you may want to make sure you have the most up-to-date version, too, which appears to be 2.0.0rc3.

---

### Post by TristanMike on 2005-09-22
You can also try running the program as sudo if you'd like. That might eliminate that pesky permissions thing.

---

### Post by erhard on 2005-09-22
[QUOTE=TristanMike]You can also try running the program as sudo if you'd like. That might eliminate that pesky permissions thing.[/QUOTE]


How exactly do i do that?

---


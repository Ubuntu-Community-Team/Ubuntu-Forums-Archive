---
title: "acces windows partitions"
date: 2005-05-19
forum: Desktop Environments
---

### Post by iano on 2005-05-19
Hi all,
i installed Ubuntu ....on a PC as dual boot with WinXP...it booted OK both..Ubuntu and Xp...I have only one problem.....i want to acces my windows partions...i edited the fstab file like this
/dev/hda1 /mnt/winc vfat  umask=0222,dmask=0000,uid=0002,gid=users,users  0 0
but I can acces only C partion from windows

the other 2 lines
/dev/hda5 /mnt/wind vfat  umask=0222,dmask=0000,uid=0002,gid=users,users  0 0
/dev/hda6 /mnt/wine vfat  umask=0222,dmask=0000,uid=0002,gid=users,users  0 0
 doesn't seems to have done their job:)...i can't see nothing in those directories from /mnt
any suggestions?
I found that command on some debian forum.... :grin: 
thanks

---

### Post by smb2004 on 2005-05-19
my /etc/fstab for my /dev/hda1 fat32 partition is:

/dev/hda1	/mnt/hda1	vfat	rw,user,auto

are you trying to mount a fat32 or ntfs?

---

### Post by poofyhairguy on 2005-05-19
I moved this to a more suitable place (your use of fstab puts you beyond a beginner in my book, take as complement).

do this command to see what drives you have:

sudo fdisk -l

then edit the fstab entry from the Ubuntu guide for that drive. Mine is hda5 for my D: drive.

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---


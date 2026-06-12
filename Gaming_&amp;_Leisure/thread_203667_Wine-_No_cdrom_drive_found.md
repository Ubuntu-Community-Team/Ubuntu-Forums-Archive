---
title: "Wine- No cdrom drive found"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by slugkilla on 2006-06-25
On all of my games wine can't find my cdrom drive. I tryed to make isos and loop that with a command told to me by someone on this forum. I can't find where that thread is, so I'll just ask again. How do you guys get wine to run large games that run off of cds?

---

### Post by digimars on 2006-06-25
I'd like to know as well, I've tried the autodetect feature under winecfg, and it does find a cdrom drive, but no matter what program I try to use in wine, it can never find the cdrom drive.

---

### Post by dtfinch on 2006-06-25
On mine I used winecfg to map /media/cdrom0 to d:. You can also try something like "ln -s /media/cdrom0 ~/.wine/dosdevices/d:"

---

### Post by digimars on 2006-06-25
Thanks for the tips, I tried both but neither worked for me.  I even checked the dosdevices folder under .wine, and sure enough it is showing the contents of my cdrom under d:, but wine just will not read from it for me when it comes to running a game or program that needs the cd.

---

### Post by slugkilla on 2006-06-25
Ok try [http://www.ubuntuforums.org/showthread.php?t=202524](http://www.ubuntuforums.org/showthread.php?t=202524)
that worked for me. Also, when you go into winecfg, try to sudo into it. I think it works better that way...

---

### Post by venkey_23 on 2010-12-17
Check and make sure that the drive is mounted. Your CD/DVD drive must be listed in /etc/mtab.

desktop:~$ cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sr0 /media/Junk udf ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077 0 0 <---- *** MY DVD Drive ****

You can mount it using the mount command or Ubuntu GUI -> Places ->(Click on your CD/DVD drive)

---

### Post by Perfect Storm on 2010-12-17
Oh my unholy necro-god!!! Thread closed due to necromancing!!!

Please check the date of a thread before replying.

---


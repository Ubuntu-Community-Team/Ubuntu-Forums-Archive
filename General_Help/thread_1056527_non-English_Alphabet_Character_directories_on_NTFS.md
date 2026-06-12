---
title: "non-English Alphabet Character directories on NTFS not accesable via Samba Share"
date: 2009-01-31
forum: General Help
---

### Post by nexist on 2009-01-31
I have a file server running Ubuntu Server 8.10. Attached to it are two USB drives formatted in NTFS (I got them when the only working system was an XP laptop). When I ssh into the fileserver, I can see & access the directories properly. When connected via a mount point running through samba (using Ubuntu 8.10) I get question marks for every non-English Alphabet character. I listen to a lot of music from Europe, Russia and Japan, so there are a lot of directories that I cannot access.

```
from a shell sshed to the fileserver:
drwxrwxrwx 1 root root  16384 2008-08-11 08:06 audialgnosis
drwxrwxrwx 1 root root  77824 2008-12-01 18:07 Because God Told Me To Do It
drwxrwxrwx 1 root root 131072 2008-11-30 16:49 Blodvargr
drwxrwxrwx 1 root root  57344 2008-12-17 07:28 Dark Obscurity
drwxrwxrwx 1 root root   4096 2008-06-13 15:52 Despair Japan
drwxrwxrwx 1 root root  40960 2008-10-17 21:06 Dualtrack
drwxrwxrwx 1 root root   4096 2008-06-03 22:37 It's Coming Out of Your Speakers
drwxrwxrwx 1 root root      0 2008-07-27 23:08 jetsiva
drwxrwxrwx 1 root root   4096 2008-10-09 21:30 Maschinenzimmer
drwxrwxrwx 1 root root      0 2008-11-03 21:57 _paul
drwxrwxrwx 1 root root 131072 2009-01-10 22:28 Sickness Abounds
drwxrwxrwx 1 root root      0 2008-07-27 23:08 Taringa!
drwxrwxrwx 1 root root      0 2008-11-04 08:05 TBM
drwxrwxrwx 1 root root  12288 2008-11-04 06:39 The Thing on the Doorstep
drwxrwxrwx 1 root root   4096 2008-08-06 00:47 Wassonii
drwxrwxrwx 1 root root      0 2008-10-17 21:22 White Ward
drwxrwxrwx 1 root root   4096 2008-07-27 23:34 &#1051;&#1086;&#1103;&#1083;&#1100;&#1085;&#1086;&#1089;&#1090;&#1080; &#1088;&#1072;&#1079;&#1083;&#1080;&#1095;&#1085;&#1099;&#1093;
```

the same directory via the symlinked samba directory on the desktop:
```
drwxrwxrwx 1 root root 0 2008-07-27 23:34 ?????????? ?????????
drwxrwxrwx 1 root root 0 2008-08-11 08:06 audialgnosis
drwxrwxrwx 1 root root 0 2008-12-01 18:07 Because God Told Me To Do It
drwxrwxrwx 1 root root 0 2008-11-30 16:49 Blodvargr
drwxrwxrwx 1 root root 0 2008-12-17 07:28 Dark Obscurity
drwxrwxrwx 1 root root 0 2008-06-13 15:52 Despair Japan
drwxrwxrwx 1 root root 0 2008-10-17 21:06 Dualtrack
drwxrwxrwx 1 root root 0 2008-06-03 22:37 It's Coming Out of Your Speakers
drwxrwxrwx 1 root root 0 2008-07-27 23:08 jetsiva
drwxrwxrwx 1 root root 0 2008-10-09 21:30 Maschinenzimmer
drwxrwxrwx 1 root root 0 2008-11-03 21:57 _paul
drwxrwxrwx 1 root root 0 2009-01-10 22:28 Sickness Abounds
drwxrwxrwx 1 root root 0 2008-07-27 23:08 Taringa!
drwxrwxrwx 1 root root 0 2008-11-04 08:05 TBM
drwxrwxrwx 1 root root 0 2008-11-04 06:39 The Thing on the Doorstep
drwxrwxrwx 1 root root 0 2008-08-06 00:47 Wassonii
drwxrwxrwx 1 root root 0 2008-10-17 21:22 White Ward
```

note that the Cyrillic characters are changed to ???? & cannot be navigated either in the shell of via the GUI. The fstab is as follows:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f736b56c-870a-45dd-8a2d-fc8cc8b220ed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=ba58f240-fec8-4f0d-be43-4efbbf169d88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
# Samba share on obelisk
//10.11.93.2/nexist /home/nexist/obelisk cifs username=nexist,password=xxxxxxx,nounix   0 0
```

How can I fix this?

---

### Post by nexist on 2009-01-31
I just copied the directory across using mc to the ext3 partition & received the same results.

---

### Post by dcstar on 2009-01-31
> **nexist said:**
> I have a file server running Ubuntu Server 8.10. Attached to it are two USB drives formatted in NTFS (I got them when the only working system was an XP laptop). When I ssh into the fileserver, I can see & access the directories properly. When connected via a mount point running through samba (using Ubuntu 8.10) I get question marks for every non-English Alphabet character. I listen to a lot of music from Europe, Russia and Japan, so there are a lot of directories that I cannot access.
.........
How can I fix this?

Have a look at this:

[http://ubuntuforums.org/showthread.php?t=728751](http://ubuntuforums.org/showthread.php?t=728751)

---

### Post by nexist on 2009-01-31
Yes! That fixed it. Thank you.

---


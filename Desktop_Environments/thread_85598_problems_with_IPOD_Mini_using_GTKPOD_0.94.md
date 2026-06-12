---
title: "problems with IPOD Mini using GTKPOD 0.94"
date: 2005-11-03
forum: Desktop Environments
---

### Post by django_xl on 2005-11-03
Hi folks,
yesterday I managed to install Breezy and started playing with my IPOD Mini. I installed GTKPOD 0.94 and when I attached the IPOD, Nautilus comes up with the contents of the IPOD.

My mount point looks like this in /etc/mtab:
**/dev/sdc2 /media/ipod vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1001,gid=1001,umask=077,iocharset=utf8 0 0**

The /media/ipod/iPod_Control/Music/ directory contains:
[B]
/media/ipod/iPod_Control/Music/F00
/media/ipod/iPod_Control/Music/F01
/media/ipod/iPod_Control/Music/F02
/media/ipod/iPod_Control/Music/F03
/media/ipod/iPod_Control/Music/F04
/media/ipod/iPod_Control/Music/F05[/B]

When I startup gtkpod (as normal user & as root) and I add files to the IPOD in a newly created playlist and click on sync I get the following error message:

Path not found: '/media/ipod/iPod_Control/Music/F06'.

Path not found: '/media/ipod/iPod_Control/Music/F07'.

Path not found: '/media/ipod/iPod_Control/Music/F08'.

Path not found: '/media/ipod/iPod_Control/Music/F09'.

Path not found: '/media/ipod/iPod_Control/Music/F10'.

Path not found: '/media/ipod/iPod_Control/Music/F11'.

Path not found: '/media/ipod/iPod_Control/Music/F12'.

Path not found: '/media/ipod/iPod_Control/Music/F13'.

Path not found: '/media/ipod/iPod_Control/Music/F14'.

Path not found: '/media/ipod/iPod_Control/Music/F15'.

Path not found: '/media/ipod/iPod_Control/Music/F16'.

Path not found: '/media/ipod/iPod_Control/Music/F17'.

Path not found: '/media/ipod/iPod_Control/Music/F18'.

Path not found: '/media/ipod/iPod_Control/Music/F19'.


A dosfschk -a /dev/sdc2 gives me:
[B]dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdc2: 255 files, 328535/986065 clusters[/B]

So what is the reason for this? What can I do to let it work as it sould be?

Brgds
Django

---

### Post by peterbrowne on 2005-11-03
i had the same problems, I just make the folders F04-F19 in the appropriate folder

---


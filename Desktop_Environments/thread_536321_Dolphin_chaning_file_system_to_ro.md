---
title: "Dolphin chaning file system to ro"
date: 2007-08-27
forum: Desktop Environments
---

### Post by Taranis on 2007-08-27
When I plug in a usb device, thumb drive, hard drive, mp3 player etc, Feisty is auto mounting no problem.  However, it is mounting as read only.. ro.

from /proc/mounts

/dev/sdb1 /media/LEXAR\040MEDIA vfat ro,nosuid,nodev,noatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,utf8 0 0

so I remount

mount -o rw,remount /dev/sdb1
and it changes to 
/dev/sdb1 /media/LEXAR\040MEDIA vfat rw,nosuid,nodev,noatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,utf8 0 0

now after I edit/delete a file on sdb1, dolphin or something, is auto changing the filesystem back to ro?

Anyone have an idea of where the change in coming from?

---


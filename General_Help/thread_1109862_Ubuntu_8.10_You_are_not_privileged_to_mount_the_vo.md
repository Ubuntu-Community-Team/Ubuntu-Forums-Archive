---
title: "Ubuntu 8.10 You are not privileged to mount the volume"
date: 2009-03-29
forum: General Help
---

### Post by VietxHieu on 2009-03-29
Just the other day I could mount my "PHONE CARD" (which is the mini micro SD) in my phone. I plug it in and "You are not privileged to mount the volume 'PHONE CARD'." I don't know what to do, but here is my fstab file And I get another error when I go to /media/ with my phone plugged in via USB. "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.". Btw I am not so great at ubuntu. Thanks for reading

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=f0e15add-09ad-4503-8602-8392520792e1 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda4
UUID=f9d4d9a4-23f3-412e-bea2-d70da11d166f /home           ext3    relatime        0       2

# /dev/sda3
UUID=fef58714-5f0a-448d-be14-67af678577c2 /opt            ext3    relatime        0       2

# /dev/sda1
UUID=d2945c3c-4288-4ddd-b692-0086a2a0e14d none            swap    sw              0       0
/dev/sdc1	/media/ipod	vfat	defaults	0 0
# /dev/sdb1
#/dev/sdb1	/alex	ext3	auto,users,rw,relatime	0 0

usbfs /proc/bus/usb usbfs		 defaults	0 0

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---


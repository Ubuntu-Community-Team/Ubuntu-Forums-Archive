---
title: "Change USB-mount options?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by MikkelMJ on 2006-06-23
Hi, I need to tell Ubuntu that it has to load all hotplug'able NTFS-USB-harddisks (also USB-sticks with NTFS filesystem) with the ufsd-filesystem and the umask=0 option, instead of the default ntfs. How do I do that?

---

### Post by rowanparker on 2006-06-23
System > Preferences > Removable Drives and Media
That should be right.

Rowan.

---

### Post by MikkelMJ on 2006-06-23
How can I change that in there? When I open it I just see 4 options for harddisks:
1) mount removeable drive on plugin
2) mount removeable media on plugin
3) åbn removable media on plugin
4) autostart programmes on new media

I don't see the option to change the default filesystem for removable drives...?

---

### Post by MikkelMJ on 2006-06-23
BTW, here a my /etc/fstab and /etc/mtab. They show that the usb-disk are really hotplugged, and that they are mounted with the default ntfs option:

**/etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/Windows  ufsd    defaults,nls=utf8,umask=0,gid=46,quiet 0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


**/etc/mtab**
/dev/hda3 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/hda1 /media/Windows ufsd rw,nls=utf8,umask=0,gid=46,quiet 0 0
/dev/sda1 /media/A ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda2 /media/B ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda3 /media/C ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

---

### Post by rowanparker on 2006-06-24
You could make a little script that mounts it and turn off auto-mount.

---

### Post by sergevn on 2006-10-18
How do you make that script?

---

### Post by rowanparker on 2006-10-18
I can't remember, it was so longer ago that I posted that.

---

### Post by ulysses222 on 2008-06-28
This is probably what you need to do:

[http://ubuntuforums.org/showthread.php?t=168221&page=1](http://ubuntuforums.org/showthread.php?t=168221&page=1)

---


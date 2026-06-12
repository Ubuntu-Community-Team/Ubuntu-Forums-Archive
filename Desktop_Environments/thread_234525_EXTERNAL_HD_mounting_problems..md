---
title: "EXTERNAL HD mounting problems."
date: 2006-08-11
forum: Desktop Environments
---

### Post by goyjuss on 2006-08-11
First off, I've been using Xubuntu for about a week or so, and am loving it.

The problem that I'm having is with my external harddrive and programs that rely on the path of it to: play music, share files online.
From time to time when I restart my external harddrive will shift paths. First it will be on /media/EXTERNAL HD and then it will be on /media/sda1.
It switches back and forth from these two all the time. I tried editing my /etc/fstab to get it loaded in another directory which I created: /fat_files, using instructions from another thread here, but that didn't solve my problem. I alo read that updating my pmount might solve the problem, but it hasn't.
I've been searching through the forums for a couple of days now and can't seem to find any thread on which my problem is discussed.
I really love Xubuntu, and the way I can customize just about anything, but if this issue doesn't have a solution I might just have to go back to WindowsXP. After spending a few days on Xubuntu though, I don't think that I really like the idea of going back to XP.

Help, please.:confused:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

/etc/mtab:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 vfat rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1 000,gid=1000,umask=077,iocharset=utf8 0 0

---


---
title: "How can I make a partition viewable from Places/Computer?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Entity on 2006-09-23
Hi, I have Ubuntu Edgy installed on my MacBook and I am able to mount the HFS+ partition without any problem.

I would simply like to make this HFS+ partition appear in nautilus, in Computer (and under Places in the gnome panel) as  a volume just like my external USB drive.

How can I do this?

Here is my current /etc/fstab file :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=642f66e0-4ee7-4fb7-97e7-38f18c8f7203	/				ext3		defaults,errors=remount-ro			0       1
# /dev/sda2
UUID=38743d18-b903-4bcb-b7fe-12c15c9e3650	/home				ext3		defaults,user_xattr				0       2
# /dev/sda4
UUID=e5a5ba2c-9af5-45b2-bbea-13793beb9167	none				swap		sw						0       0
/dev/hda				        /media/cdrom0			udf,iso9660	user,noauto					0       0
/dev/sda3                                       /media/Macintosh\040HD          hfsplus         rw,user,nosuid,auto,uid=1000,gid=1000		0       0
```
I also attached a screenshot of where I would like to see this partition appear as "Macintosh HD"

Many thanks for your time and help.

---


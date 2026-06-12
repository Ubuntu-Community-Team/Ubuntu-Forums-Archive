---
title: "Details of Ubuntu fstab"
date: 2009-03-08
forum: General Help
---

### Post by ijustwantyourhalf on 2009-03-08
Hi All,

I originally posted a question to the gnome area but I think that this is more of an OS question than a desktop question

Here is my problem:

Installed ubuntu 8.10 on a 500g sata drive that I had partitioned myself (boot,swap,/,/home)
Later I installed a 160g drive that has my music on it in two partitions.

I edited /etc/fstab to add the new partitions


Everything works great! Music1 and Music2 are mounted in /home/blue/Music when the computer boots up.

[I]They also show up on the desktop as mounted volumes.
[/I]
I don't want them to show up on the desktop. I don't wand any drive that is mounted through /etc/fstab to show up on the desktop. My original 500g install drive doesn't show up. Why does the one that I added later?

I dont want to uncheck the volumes_visible because When I plug in a camera or flash drive I want the icon on the desktop so wife/kids see it to unmount it.

Is there some fstab syntax that I am not understanding?

Thanks in advance for any help,

Don


fstab looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=76a05d6c-fd38-4a22-8a83-bb2d33f13217 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=6f3b64ab-5bce-45d9-8e25-40e81b4bf244 /boot           ext2    relatime        0       2
# /dev/sda4
UUID=930cb508-76d8-4836-801b-1025df2c9f07 /home           ext3    relatime        0       2
# /dev/sda3
UUID=175c2d90-7743-4375-aff5-979133d29ea4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda1
UUID=c7dc7ac2-2cb7-46d0-bed0-f8b5ea3cf144	/home/blue/Music/Music1			ext3	defaults	0	2
#/dev/sda2
UUID=89f9c1aa-0de8-4ff3-a86a-8411a6d7de25	/home/blue/Music/Music2			ext3	defaults	0	2


---

### Post by heindsight on 2009-03-08
Unless you uncheck the volumes_visible option in gconf, GNOME will display any filesystems mounted under your home directory on your desktop. The only change you could make to /etc/fstab to stop those filesystems showing up on your desktop, is to mount them somewhere else and then put symlinks to the mountpoints under your home directory.

---


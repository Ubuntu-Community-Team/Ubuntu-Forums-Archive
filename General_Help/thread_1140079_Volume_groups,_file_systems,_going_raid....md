---
title: "Volume groups, file systems, going raid..."
date: 2009-04-27
forum: General Help
---

### Post by Th3Professor on 2009-04-27
I wasn't really sure where to put these questions, I figured maybe in install/upgrade forums but that's not right, it's really more of a general thing..

Okay, questions are below...

I have 5 hard drives:
1= OS (all boots and primary system files)
2,3,4= storage (raid5 & lvm)
5= external (movable storage)

Partitions:
sda1 = linux = /boot
sda2 = windows vista (with fuse, which isn't working right now, not sure why)
sda3 = solaris boot (not currently set-up)
sda5 = linux (system files only) = /
sda6 = linux (workspace) = /studio/workspace
sda7 = swap (striped priority with sda8 )
sda8 = swap (striped priority with sda7)
sda9 = solaris = not currently set-up
sda10 = linux (for secondary linux system, like gentoo) = not currently set-up
sdb1 = linux raid
sdc1 = linux raid
sdd1 = linux raid
sdi1 = vfat (fat32 default), external storage, used to read as sde1 (that's odd)

Regarding volumes...

My non-OS internal disks (sdb, sdc, sdd) are set-up with linux soft raid (raid5, 128k chunk) via mdadm (/dev/md0), and they're using lvm (matching block/chunk/etc.) for use with 3 separate volume groups (/dev/mapper/vg0-vault (xfs), /dev/mapper/vg0-zone (ext3), /dev/mapper/vg0-nomad (ext3)). The "vault" is primarily storage, while my intention with "zone" is for unix non-boot type files (initially solaris, alternately openbsd), and my intention with "nomad" is for alternate linux non-boot type files (like gentoo or slackware).


[LIST=1]
[*] Can I use those volume groups with any of those systems?
[*]If I cannot use those groups with any of the systems (perhaps due to lvm), how might I apply my raid5 space to those systems (perhaps without lvm)?
[*]Is it possible to set up the raid5 on all 3 of those disks while only using lvm on part of the space, reserving non-lvm (but still raid5) space for use with other systems?
[*]It looked like xfs works really well with my raid5 set-up, is there any real advantage (or disadvantage) to using that over ext3 with this kind of set-up?
[/LIST]
 thanks :)

---

### Post by Th3Professor on 2009-04-28
bump

---

### Post by Th3Professor on 2009-04-29
bump

---

### Post by Th3Professor on 2009-05-01
bump

---

### Post by Th3Professor on 2009-05-02
bump #4

---


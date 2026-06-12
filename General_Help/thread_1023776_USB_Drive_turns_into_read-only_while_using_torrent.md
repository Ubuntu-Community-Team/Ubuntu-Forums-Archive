---
title: "USB Drive turns into read-only while using torrent."
date: 2008-12-28
forum: General Help
---

### Post by lhong1987 on 2008-12-28
"torrent paused: disk write error, open failed: '/media/drive/xxxx.xxx'. Read-only file system"

I start the torrent download with deluge-torrent and I go away for about 10 minutes.
When I come back, above message is displayed and the download pauses.

This is my fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=736288ef-1826-4e24-8e9b-8fd47fd0ed65 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=291695cf-4140-88aa-550b-707a4f74bc01 none            swap    sw              0       0

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
none /var/cache unionfs dirs=/tmp:/var/cache=ro 0 0


---

### Post by aurelieng on 2008-12-28
Perhaps you have errors on your partition, and your filesystem is automatically protected by being silently remounted read only. You should try to unmount the partition, run fsck, remount it read-write, and check if your problem still happens.

---

### Post by HyperHacker on 2008-12-28
Disks becoming read-only usually means their filesystem is corrupt.

---

### Post by dcstar on 2008-12-28
> **lhong1987 said:**
> "torrent paused: disk write error, open failed: '/media/drive/xxxx.xxx'. Read-only file system"
.......

External drives are mounted in /media, as the others have said you probably have a corrupt filesystem in the external drive you are writing to.

It has nothing whatsover to do with your fstab if it is an external drive.

---


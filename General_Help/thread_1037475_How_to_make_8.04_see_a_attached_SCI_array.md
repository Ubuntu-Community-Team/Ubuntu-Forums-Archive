---
title: "How to make 8.04 see a attached SCI array?"
date: 2009-01-11
forum: General Help
---

### Post by Linuxwho? on 2009-01-11
How do I add a new disk to my puter? Its a scsi array on a scsi cable attached storage..using 8.04

I dont see it in any form of disk manager or know its identity. How do I know what command with or what to fdisk? It is an attached array via scsi cable. Is there a command to identify it before using the fdisk command?  I already craeted it using smart start cd for compaq but it duznt see it.

This is what I tried:
owner@owner-desktop:~$ sudo fdisk -l
owner@owner-desktop:~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda (for the first IDE disk)
or: fdisk /dev/sdc (for the third SCSI disk)
or: fdisk /dev/eda (for the first PS/2 ESDI drive)
or: fdisk /dev/rd/c0d0 or: fdisk /dev/ida/c0d0 (for RAID devices)
...
owner@owner-desktop:~$ fdisk /dev/sda

Unable to open /dev/sda
owner@owner-desktop:~$ fdisk /dev/sdb

Unable to open /dev/sdb

---



I tried another command but I dunno what he output means ...

"owner@owner-desktop:~$ dmesg |grep scsi
[ 4.407330] scsi0 : pata_serverworks
[ 4.407628] scsi1 : pata_serverworks
[ 4.752299] scsi 0:0:0:0: CD-ROM COMPAQ CD-224E A.8D PQ: 0 ANSI: 5
[ 4.777970] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[ 4.815103] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[ 4.815328] sr 0:0:0:0: Attached scsi CD-ROM sr0

AND--->

"owner@owner-desktop:~$ MAKEDEV sdb /*
mknod: `sdb-': Operation not permitted
makedev sdb b 8 16 root disk 0660: failed
mknod: `sdb1-': Operation not permitted
makedev sdb1 b 8 17 root disk 0660: failed
mknod: `sdb2-': Operation not permitted
makedev sdb2 b 8 18 root disk 0660: failed
mknod: `sdb3-': Operation not permitted
makedev sdb3 b 8 19 root disk 0660: failed
mknod: `sdb4-': Operation not permitted
makedev sdb4 b 8 20 root disk 0660: failed
mknod: `sdb5-': Operation not permitted
makedev sdb5 b 8 21 root disk 0660: failed
mknod: `sdb6-': Operation not permitted
makedev sdb6 b 8 22 root disk 0660: failed
mknod: `sdb7-': Operation not permitted
makedev sdb7 b 8 23 root disk 0660: failed
mknod: `sdb8-': Operation not permitted
makedev sdb8 b 8 24 root disk 0660: failed
mknod: `sdb9-': Operation not permitted
makedev sdb9 b 8 25 root disk 0660: failed
mknod: `sdb10-': Operation not permitted
makedev sdb10 b 8 26 root disk 0660: failed
mknod: `sdb11-': Operation not permitted
makedev sdb11 b 8 27 root disk 0660: failed
mknod: `sdb12-': Operation not permitted
makedev sdb12 b 8 28 root disk 0660: failed
mknod: `sdb13-': Operation not permitted
makedev sdb13 b 8 29 root disk 0660: failed
mknod: `sdb14-': Operation not permitted
makedev sdb14 b 8 30 root disk 0660: failed
mknod: `sdb15-': Operation not permitted
makedev sdb15 b 8 31 root disk 0660: failed
/sbin/MAKEDEV: don't know how to make device "/bin"

---

### Post by nshank on 2009-09-14
Don't know if you already got a response, or if you've already found the answer. 

owner@owner-desktop:~$ MAKEDEV sdb /*

Try: sudo MAKEDEV sdb /*

---


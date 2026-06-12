---
title: "XFCE and my NTFS mount won't show"
date: 2008-04-26
forum: Desktop Environments
---

### Post by majician on 2008-04-26
noticed this not just with ubuntu but with mandriva too. 
heres the scenario. I use Hd1 for my linux,  Hd2 is my WinXP partition, and Hd3 is a usb 500 gig. I usually get on GNOME first then install XFCe 4.4.2

everytime i go on xfce i notice i only see my usb 500 gig hd mounted while my Hd2 (winxp) never gets mounted. It mounts in Gnome though 

This is for both distro's so i know it must be a Xfce problem..

Any ideas? Thanks

---

### Post by p_quarles on 2008-04-26
Are you sure that the NTFS drive isn't mounted, or is it simply not showing up on the desktop? Anyway, if you could provide the output of these terminal commands, some light may be shed on the issue:
```
dh -h
```
```
cat /etc/fstab
```
```
sudo fdisk -l
```

---

### Post by majician on 2008-04-26
dh -h
bash: dh: command not found


 cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=35a349b7-7034-45b3-8b85-36b43619f869 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=13e65387-0294-44e3-a9dd-62d55c41c57b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


 sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe554e554

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7679    61681536    7  HPFS/NTFS
/dev/sda2            7680       38913   250887105    5  Extended
/dev/sda5            7680       38913   250887073+   7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000146e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19271   154794276   83  Linux
/dev/sdb2           19272       20023     6040440    5  Extended
/dev/sdb5           19272       20023     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00090dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS




Ok your right i think it mounted it, but how do i show it? thanks for the help

---

### Post by majician on 2008-04-26
i mean it already detects it, i just gotta mount it

---

### Post by majician on 2008-04-26
Got it, i see i had to use sudo fdisk -l to list my avail hd's

then whatever i wanna mount

mount -t ntfs /dev/**hda1** /mnt/ntfs

---

### Post by p_quarles on 2008-04-26
Yeah, that'll work. You can also add a line to /etc/fstab to make the volume mount automatically. 

Sorry about the typo: that should have been "df -h", not "dh -h".

---


---
title: "[SOLVED] Why do CDs mount in different places?"
date: 2008-12-26
forum: General Help
---

### Post by redsoxreed on 2008-12-26
Hi.  Sometimes, when I put a cd in the drive, it mounts to /media/cdrom0.  Other times, a folder with the name of the disk is created in /media, and it mounts there instead.  Why is this?  Why don't they always use cdrom0 as a mount point?

---

### Post by Monotoko on 2008-12-26
They should do...thats interesting, /media/disk is usually reserved for hard-disks

---

### Post by mc4man on 2008-12-26
> a folder with the name of the disk is created in /media, and it mounts there instead

When media mounts to /media/<volume label> that normally indicates there is no fstab entry for the device (in this case your cd/dvd drive.

When it mounts to /media/cdrom0 it's been recognized in fstab. (again normally your cd/dvd drive

The exception would be audio cd's which aren't actually 'mounted', but have a location .gvfs cdda mount on /dev/scdx

 Run this and post your fstab file

```
cat /etc/fstab
```

Maybe also 
```
sudo lshw -C disk
```

---

### Post by dcstar on 2008-12-27
> **redsoxreed said:**
> Hi.  Sometimes, when I put a cd in the drive, it mounts to /media/cdrom0.  Other times, a folder with the name of the disk is created in /media, and it mounts there instead.  Why is this?  Why don't they always use cdrom0 as a mount point?

Disks with labelled partitions are mounted with the partition name, those without names are not.

---

### Post by jerome1232 on 2008-12-27
> **dcstar said:**
> Disks with labelled partitions are mounted with the partition name, those without names are not.

This was my exact thought, I think they are treated the exact same way as hard disks, file systems with labels get mounted at /media/labelname, those without labels will get mounted at /media/cdrom0 (Well in the case of a hard disc drive it would be at /media/disk but you get the idea)

---

### Post by redsoxreed on 2008-12-27
Okay, but this poses a problem with how I use wine.  In winecfg, I set up a virtual drive D: which corresponded to cdrom0.  This way, I wouldn't get messages asking me to insert the original disk when running a game.

```
reed@overlord:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2b2267cd-5dac-4df0-bec4-d2319928a2b5 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=b25cbc65-79f5-4a98-bf44-006c94339f12 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

```
reed@overlord:~$ sudo lshw -C disk
[sudo] password for reed: 
  *-disk                  
       description: ATA Disk
       product: ExcelStor Techno
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: P22O
       serial: PV7904Q4B1P4JB
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005d3a7
  *-cdrom
       description: DVD-RAM writer
       product: DVD Writer 1035r
       vendor: HP
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Disk1
       version: NH21
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/Disk1
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos

```

---

### Post by mc4man on 2008-12-27
What release of ubuntu are you using?

In a maximized terminal run this and post

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

```
sudo fdisk -l
```

Also your going to want to edit fstab, For the moment run the above. What's on your 2nd hard drive?

This is wrong in fstab
> /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Should be 

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by redsoxreed on 2008-12-27
```
reed@overlord:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# HP_DVD_Writer_1035r (pci-0000:00:06.0-ide-0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:1", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:1", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:1", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-ide-0:1", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVD_Writer_1035r (pci-0000:00:06.0-scsi-0:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"

```

```
reed@overlord:~$ sudo fdisk -l
[sudo] password for reed: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d3a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18752   150625408+  83  Linux
/dev/sda2           18753       19457     5662912+   5  Extended
/dev/sda5           18753       19457     5662881   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204819+  ee  GPT
/dev/sdb2   *          26       30402   243993744    c  W95 FAT32 (LBA)

```

My second hard drive is external, that's where I keep most of my movies, music, and backups.  (It's a lot bigger than my internal hard drive)

---

### Post by mc4man on 2008-12-27
run this 
```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
and delete the 2 entries, leave it like this

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

then run
 ```
gksudo gedit /etc/fstab
```
change the line as mentioned in my edit in previous post so it looks like this

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2b2267cd-5dac-4df0-bec4-d2319928a2b5 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=b25cbc65-79f5-4a98-bf44-006c94339f12 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



Then reboot _without your external drive connected_

---

### Post by redsoxreed on 2008-12-27
I did just that and it worked! :)  I popped in a CD and it mounted in cdrom0 just as it should.  Thanks!

---

### Post by mc4man on 2008-12-27
Great

If you want run sudo lshw -C disk again and your logical names for the cd/dvd drive should be back to the defaults
/dev/scd0
/dev/dvd  (was /dev/dvd1
/dev/cdrom (was /dev/cdrom1
mounting at /media/cdrom0

If they're still /dev/dvd1 : /dev/cdrom1 no real issue, just remember most media players will default to /dev/dvd and /dev/cdrom and make adjustments in the players settings when needed

---

### Post by redsoxreed on 2008-12-27
I'll keep that in mind.  Thanks!

---


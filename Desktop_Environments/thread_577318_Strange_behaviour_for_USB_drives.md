---
title: "Strange behaviour for USB drives"
date: 2007-10-16
forum: Desktop Environments
---

### Post by SunWukong_fr on 2007-10-16
Hello folks !

My system is composed of 2 IDE HD, 80Go each that are /dev/sdb and /dev/sdc.
Recently, I was given a 160Go SATA HD which appears in /dev/sda.
Motherboard is Asus P5B, it boots on IDE.

Given that fresh extra space available for backup and willing to test Gutsy, I installed a Kubuntu 7.10 beta 64 bits. Thus, no upgrade, but a fresh start.

But some troubles appeared and here is one :
I've got to USB HD.
One 60 Go with a single FAT32.
One 320 Go with 3 partitions : 512Mo fat32, 1Go ext2, all the rest is ext2.

When I boot the computer, the USB HD are NOT mounted automatically as they should be. And if I unplug them, and hot-plug them again, they are mounted correctly.

I've looked everywhere but the right place to find a clue.

Here're some files and logs :
[FONT="Courier New"][COLOR="Blue"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb6
UUID=394f2d3e-3d08-4a1f-900e-977a334cfc0a / xfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb1
UUID=3ca10332-ce40-496b-b848-9fa6bb9e4b34 /boot ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdc1
UUID=b43a0100-acfe-47e1-af8f-70d75c3d9c2c /home xfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=e4e8b100-c27e-433c-aa08-acc8a3a99957 /media/Extras ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb2
UUID=3cbc8170-77fa-43b9-b521-23960dc3b15c /usr xfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb5
UUID=1f0c0526-0afe-4cd4-a7f2-c254f5753dca none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
# UNCONFIGURED FSTAB FOR BASE SYSTEM[/COLOR][/FONT]

Here is /etc/mtab
[FONT="Courier New"][COLOR="Blue"]
/dev/sdb6 / xfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-12-generic/volatile tmpfs rw 0 0
/dev/sdb1 /boot ext3 rw 0 0
/dev/sdc1 /home xfs rw 0 0
/dev/sda1 /media/Livres ext3 rw 0 0
/dev/sdb2 /usr xfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
[/COLOR][/FONT]

Here's an extract from dmeg

[FONT="Courier New"][COLOR="Blue"]
[   88.476212] usb-storage: device scan complete
[   88.476270] usb-storage: device scan complete
[   88.476875] scsi 5:0:0:0: Direct-Access     USB 2.0  Storage Device   0100 PQ: 0 ANSI: 0 CCS
[   88.511562] scsi 4:0:0:0: Direct-Access     WD       3200JB External  0107 PQ: 0 ANSI: 0
[   88.512671] sd 4:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[   88.513547] sd 4:0:0:0: [sdd] Write Protect is off
[   88.513548] sd 4:0:0:0: [sdd] Mode Sense: 03 00 00 00
[   88.513550] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   88.514418] sd 4:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[   88.515295] sd 4:0:0:0: [sdd] Write Protect is off
[   88.515297] sd 4:0:0:0: [sdd] Mode Sense: 03 00 00 00
[   88.515298] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   88.515301]  sdd: sdd1 sdd2 sdd3
[   88.515970] sd 4:0:0:0: [sdd] Attached SCSI disk
[   88.515996] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   88.516831] sd 5:0:0:0: [sde] 117210240 512-byte hardware sectors (60012 MB)
[   88.517454] sd 5:0:0:0: [sde] Write Protect is off
[   88.517456] sd 5:0:0:0: [sde] Mode Sense: 08 00 00 00
[   88.517458] sd 5:0:0:0: [sde] Assuming drive cache: write through
[   88.518331] sd 5:0:0:0: [sde] 117210240 512-byte hardware sectors (60012 MB)
[   88.518955] sd 5:0:0:0: [sde] Write Protect is off
[   88.518956] sd 5:0:0:0: [sde] Mode Sense: 08 00 00 00
[   88.518958] sd 5:0:0:0: [sde] Assuming drive cache: write through
[   88.518960]  sde: sde1
[   88.878645] sd 5:0:0:0: [sde] Attached SCSI disk
[   88.878697] sd 5:0:0:0: Attached scsi generic sg5 type 0
[/COLOR][/FONT]

Here's an what lsusb returns :

[FONT="Courier New"][COLOR="Blue"]
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 045e:00e5 Microsoft Corp.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 08e6:3437 Gemplus GemPC Twin SmartCard Reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0402:5637 ALi Corp. M5637 IDE Controller
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1058:0901 Western Digital Technologies, Inc.
Bus 001 Device 001: ID 0000:0000
[/COLOR][/FONT]

these commands have no effects on the problem : USB HD still aren't mounted
[FONT="Courier New"]sudo /etc/init.d/hal restart
sudo /etc/init.d/hal force-reload
sudo /etc/init.d/udev reload
sudo /etc/init.d/udev restart
[/FONT]

Here's the view from /proc/partitions :

[COLOR="Blue"][FONT="Courier New"]major minor  #blocks  name

   8     0  156250000 sda
   8     1  156248158 sda1
   8    16   78150744 sdb
   8    17     497983 sdb1
   8    18   24410767 sdb2
   8    19    7815622 sdb3
   8    20          1 sdb4
   8    21    2931831 sdb5
   8    22   42491893 sdb6
   8    32   78150744 sdc
   8    33   73923066 sdc1
   8    34    4225095 sdc2
   8    48   58605120 sdd
   8    49   58597056 sdd1
   8    64  312571224 sde
   8    65     522081 sde1
   8    66    1052257 sde2
   8    67  310994302 sde3[/FONT]
[/COLOR]

Thus, the USB HDs are detected, devices are created, but nothing is mounted.

Here're some events in /var/log/udev concerning /dev/sde
(similar events concerning /dev/sdd are present too)
[COLOR="Blue"][FONT="Courier New"]UEVENT[1192520790.196435] add      /block/sde (block)
ACTION=add
DEVPATH=/block/sde
SUBSYSTEM=block
SEQNUM=1918
MINOR=64
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UEVENT[1192520790.196440] add      /block/sde/sde1 (block)
ACTION=add
DEVPATH=/block/sde/sde1
SUBSYSTEM=block
SEQNUM=1919
MINOR=65
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UEVENT[1192520790.196444] add      /block/sde/sde2 (block)
ACTION=add
DEVPATH=/block/sde/sde2
SUBSYSTEM=block
SEQNUM=1920
MINOR=66
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UEVENT[1192520790.196449] add      /block/sde/sde3 (block)
ACTION=add
DEVPATH=/block/sde/sde3
SUBSYSTEM=block
SEQNUM=1921
MINOR=67
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UDEV  [1192520790.478153] add      /block/sde/sde1 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sde/sde1
SUBSYSTEM=block
SEQNUM=1919
MINOR=65
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVTYPE=partition
ID_VENDOR=WD
ID_MODEL=3200JB_External
ID_REVISION=0107
ID_SERIAL=WD_3200JB_External_57442D5743414D5233323733323936-0:0
ID_SERIAL_SHORT=57442D5743414D5233323733323936
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=380F-E6DD
ID_FS_UUID_ENC=380F-E6DD
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
DEVNAME=/dev/sde1
DEVLINKS=/dev/disk/by-id/usb-WD_3200JB_External_57442D5743414D5233323733323936-0:0-part1 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/380F-E6DD

UDEV  [1192520790.599089] add      /block/sde/sde2 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sde/sde2
SUBSYSTEM=block
SEQNUM=1920
MINOR=66
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVTYPE=partition
ID_VENDOR=WD
ID_MODEL=3200JB_External
ID_REVISION=0107
ID_SERIAL=WD_3200JB_External_57442D5743414D5233323733323936-0:0
ID_SERIAL_SHORT=57442D5743414D5233323733323936
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext2
ID_FS_VERSION=1.0
ID_FS_UUID=a7cfee52-0e8f-416f-8901-b7fadb198722
ID_FS_UUID_ENC=a7cfee52-0e8f-416f-8901-b7fadb198722
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
DEVNAME=/dev/sde2
DEVLINKS=/dev/disk/by-id/usb-WD_3200JB_External_57442D5743414D5233323733323936-0:0-part2 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0-part2 /dev/disk/by-uuid/a7cfee52-0e8f-416f-8901-b7fadb198722


UDEV  [1192520790.543927] add      /block/sde/sde3 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sde/sde3
SUBSYSTEM=block
SEQNUM=1921
MINOR=67
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host4/target4:0:0/4:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVTYPE=partition
ID_VENDOR=WD
ID_MODEL=3200JB_External
ID_REVISION=0107
ID_SERIAL=WD_3200JB_External_57442D5743414D5233323733323936-0:0
ID_SERIAL_SHORT=57442D5743414D5233323733323936
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext2
ID_FS_VERSION=1.0
ID_FS_UUID=840caf0c-f4eb-4c57-a0b7-268b458da15a
ID_FS_UUID_ENC=840caf0c-f4eb-4c57-a0b7-268b458da15a
ID_FS_LABEL=myBook
ID_FS_LABEL_ENC=myBook
ID_FS_LABEL_SAFE=myBook
DEVNAME=/dev/sde3
DEVLINKS=/dev/disk/by-id/usb-WD_3200JB_External_57442D5743414D5233323733323936-0:0-part3 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0-part3 /dev/disk/by-uuid/840caf0c-f4eb-4c57-a0b7-268b458da15a /dev/disk/by-label/myBook

[/FONT][/COLOR]


Thanks for your help :-)

---

### Post by SunWukong_fr on 2007-10-17
No idea ?

---

### Post by SunWukong_fr on 2007-10-17
up

---


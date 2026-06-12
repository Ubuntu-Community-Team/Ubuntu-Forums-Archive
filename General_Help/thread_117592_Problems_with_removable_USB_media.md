---
title: "Problems with removable USB media"
date: 2006-01-15
forum: General Help
---

### Post by Durham on 2006-01-15
I'm using Kubuntu 5.10, and when I plug in an USB-stick I get this message from konqueror:

An error occurred while loading media:/hda1:
The file or folder media:/hda1 does not exist.

The USB stick is obviously mounted since I'm able access it trough the shell.

lsusb tells me this:
[INDENT][SIZE="1"]Bus 004 Device 032: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0 (256MB)
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/SIZE][/INDENT]

I was able to mount the memorystick when I put a new device on the desktop  

------------

Next problem is my Asono Mica MP3 player
I windows xp it pops up as it should, but on my laotop with Kubuntu nothing happens. 

lsusb gives me no hints:
[INDENT][SIZE="1"]Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
[/SIZE][/INDENT]

Output of dmesg:
[INDENT][SIZE="1"]M01:~$ dmesg|tail
[4368871.243000]  /dev/scsi/host4/bus0/target0/lun0: p1
[4368871.246000] Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0
[4368871.249000] usb-storage: device scan complete
[4368873.539000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4369293.478000] usb 4-4: USB disconnect, address 32
[4369422.330000] usb 2-2: new full speed USB device using uhci_hcd and address 58
[4369427.392000] usb 2-2: can't set config #1, error -71
[4369428.529000] usb 2-2: new full speed USB device using uhci_hcd and address 60
[4369433.605000] usb 2-2: can't set config #1, error -71
[4369434.529000] usb 2-2: new full speed USB device using uhci_hcd and address 62[/SIZE][/INDENT]

fdisk shows this:
[INDENT][SIZE="1"]sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4774    38347123+  83  Linux
/dev/hda2            4775        4864      722925    5  Extended
/dev/hda5            4775        4864      722893+  82  Linux swap / Solaris[/SIZE][/INDENT]

---

### Post by Gowator on 2006-01-15
Did you update udev ? (adept or synaptic)

I think its broken in the latest version 

My CF refuses to mount at all now... I think the only fix it possibly a reinstall.

see also 

[http://www.ubuntuforums.org/showthread.php?t=117560](http://www.ubuntuforums.org/showthread.php?t=117560)

---


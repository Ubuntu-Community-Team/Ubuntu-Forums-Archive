---
title: "External Harddrive - Okay on XP, not on Ubuntu"
date: 2009-01-10
forum: General Help
---

### Post by abelianjeff on 2009-01-10
I had been using my FAT32-formatted external USB harddrive for several months flawlessly with ubuntu. Recently, however, ubuntu stopped recognizing the hard drive.  I plugged the hard drive into a computer running XP, and it recognized it with no problem. How can I fix it so that my ubuntu laptop can recognize the hard drive again?

Thanks!

Edit: On second thought, it's possible that the hard drive is formatted NTFS. I don't recall.

---

### Post by dcstar on 2009-01-10
> **abelianjeff said:**
> I had been using my FAT32-formatted external USB harddrive for several months flawlessly with ubuntu. Recently, however, ubuntu stopped recognizing the hard drive.  I plugged the hard drive into a computer running XP, and it recognized it with no problem. How can I fix it so that my ubuntu laptop can recognize the hard drive again?

Thanks!

Edit: On second thought, it's possible that the hard drive is formatted NTFS. I don't recall.

Do a fsck on it.

---

### Post by abelianjeff on 2009-01-10
> **dcstar said:**
> Do a fsck on it.

Hi David,

How do I do this (note: on XP, since the drive is not recognized on Ubuntu), and what will this do? Will there be some sort of output for me to interpret?

---

### Post by Sherlock Holmes on 2009-01-10
It doesn't matter if it's ntfs. ntfs-3g should do it. I would lsusb first, to see if it's getting recognized at all. One of my external hard drives does not respond to Ubuntu, but the one I'm using now obviously does. It may have had some error that prevents it from being used.

Isn't it just fsck -a /media/<name>?
(Someone correct me if I'm wrong)

---

### Post by abelianjeff on 2009-01-10
> **Sherlock Holmes said:**
> It doesn't matter if it's ntfs. ntfs-3g should do it. I would lsusb first, to see if it's getting recognized at all. One of my external hard drives does not respond to Ubuntu, but the one I'm using now obviously does. It may have had some error that prevents it from being used.

Isn't it just fsck -a /media/<name>?
(Someone correct me if I'm wrong)

Here's the output of lsusb after plugging in my harddrive:


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So the harddrive is showing up. What can I do from here?

---

### Post by Sherlock Holmes on 2009-01-10
I THINK (not sure) it's "fsck -a <hard-drive location>"

---

### Post by abelianjeff on 2009-01-10
Sorry for all of the stupid questions, but how do I find the hard drive's location? Is it given somewhere in that lsusb output?

---

### Post by Sherlock Holmes on 2009-01-10
I would just check under gparted if it exists (I'm new to Ubuntu too, really). I think it's /dev/sdb or something. Try gparted. Also, did you safely remove from windows?

---

### Post by abelianjeff on 2009-01-10
> **Sherlock Holmes said:**
> I would just check under gparted if it exists (I'm new to Ubuntu too, really). I think it's /dev/sdb or something. Try gparted. Also, did you safely remove from windows?

Yep, I made sure to safely remove from windows.

GParted is failing to complete the "Scanning All Devices" step of start-up. Strange...

---

### Post by domoso on 2009-01-10
You could run dmesg | grep USB. It may list what device it's mapped to. Or sudo fdisk -l may help you find it.

---

### Post by abelianjeff on 2009-01-10
> **domoso said:**
> You could run dmesg | grep USB. It may list what device it's mapped to. Or sudo fdisk -l may help you find it.

Here are the outputs:

[INDENT]jeff@jeff-laptop:~$ dmesg | grep USB
[    2.723716] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.731586] USB Universal Host Controller Interface driver v3.0
[    2.754870] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.755097] hub 1-0:1.0: USB hub found
[    2.856429] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.856600] hub 2-0:1.0: USB hub found
[    2.960362] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.960540] hub 3-0:1.0: USB hub found
[    3.064591] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.064768] hub 4-0:1.0: USB hub found
[    3.168344] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.168523] hub 5-0:1.0: USB hub found
[74645.096046] usb 1-5: new high speed USB device using ehci_hcd and address 2
[74646.842687] Initializing USB Mass Storage driver...
[74646.845515] scsi2 : SCSI emulation for USB Mass Storage devices
[74646.885276] USB Mass Storage support registered.
[75384.532027] usb 1-5: USB disconnect, address 2
[75386.860049] usb 1-5: new high speed USB device using ehci_hcd and address 3
[75387.034152] scsi3 : SCSI emulation for USB Mass Storage devices
[75619.563941] usb 1-5: USB disconnect, address 3
[75621.892045] usb 1-5: new high speed USB device using ehci_hcd and address 4
[75622.090936] scsi4 : SCSI emulation for USB Mass Storage devices
[80334.113665] usb 1-5: USB disconnect, address 4
[82427.681151] usb 1-5: new high speed USB device using ehci_hcd and address 5
[82428.000929] scsi5 : SCSI emulation for USB Mass Storage devices

jeff@jeff-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa5bfa5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8d55133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7296    58597087+   f  W95 Ext'd (LBA)
/dev/sdb5               2        7296    58597056    b  W95 FAT32[/INDENT]


How do I interpret this and find the location of my USB device?

Thanks!

---

### Post by domoso on 2009-01-11
Hmmm, I'm not seeing anything helpful in what you posted.

Try this. Disconnect the usb drive. Type dmesg then press enter. Note what the last part says because you'll run it again and examine the difference. Now reconnect the drive. Wait about 15 - 30 seconds. The reason for the wait is sometimes it can take the os time to do what it needs to do with the drive. Now type dmesg and press enter again. You're looking for something like this, it should be at the very end of the screen output for dmesg:

[  496.316126] usb 3-3.4.3: new high speed USB device using ehci_hcd and address 10
[  496.454608] usb 3-3.4.3: configuration #1 chosen from 1 choice
[  496.485480] scsi5 : SCSI emulation for USB Mass Storage devices
[  496.486290] usb-storage: device found at 10
[  496.486296] usb-storage: waiting for device to settle before scanning

AND THIS

[  501.484266] usb-storage: device scan complete
[  501.485149] scsi 5:0:0:0: Direct-Access     ST980825 AS                    PQ: 0 ANSI: 2 CCS
[  501.503121] sd 5:0:0:0: [sde] 156301488 512-byte hardware sectors (80026 MB)
[  501.504459] sd 5:0:0:0: [sde] Write Protect is off
[  501.504466] sd 5:0:0:0: [sde] Mode Sense: 34 00 00 00
[  501.504470] sd 5:0:0:0: [sde] Assuming drive cache: write through
[  501.543153] sd 5:0:0:0: [sde] 156301488 512-byte hardware sectors (80026 MB)
[  501.548968] sd 5:0:0:0: [sde] Write Protect is off
[  501.548978] sd 5:0:0:0: [sde] Mode Sense: 34 00 00 00
[  501.548981] sd 5:0:0:0: [sde] Assuming drive cache: write through
[  501.549517]  sde: sde1
[  501.567184] sd 5:0:0:0: [sde] Attached SCSI disk
[  501.567516] sd 5:0:0:0: Attached scsi generic sg5 type 0


This should tell you if the drive is being detected and if it's being mapped (which you say it isn't) and it should give you error messages as well. One thing I've noticed with using usb drives between Ubuntu and Windows is a "dirty" drive. Ubuntu will complain that a drive is "dirty" and will refuse to mount it automatically. The reason is that Windows doesn't unmount the drive in the way Ubuntu requires. The "clean" it you reconnect the drive in Windows, go to the disk manager and remove the letter assigned to the drive (this is unmounting in Windows). Then reboot into Ubuntu and it will mount. But you should be getting some rather aggravating errors in Ubuntu everytime you connect the drive, if it's dirty.

---

### Post by theozzlives on 2009-01-11
> **abelianjeff said:**
> Here are the outputs:

[INDENT]jeff@jeff-laptop:~$ dmesg | grep USB
[    2.723716] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.731586] USB Universal Host Controller Interface driver v3.0
[    2.754870] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.755097] hub 1-0:1.0: USB hub found
[    2.856429] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.856600] hub 2-0:1.0: USB hub found
[    2.960362] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.960540] hub 3-0:1.0: USB hub found
[    3.064591] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.064768] hub 4-0:1.0: USB hub found
[    3.168344] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.168523] hub 5-0:1.0: USB hub found
[74645.096046] usb 1-5: new high speed USB device using ehci_hcd and address 2
[74646.842687] Initializing USB Mass Storage driver...
[74646.845515] scsi2 : SCSI emulation for USB Mass Storage devices
[74646.885276] USB Mass Storage support registered.
[75384.532027] usb 1-5: USB disconnect, address 2
[75386.860049] usb 1-5: new high speed USB device using ehci_hcd and address 3
[75387.034152] scsi3 : SCSI emulation for USB Mass Storage devices
[75619.563941] usb 1-5: USB disconnect, address 3
[75621.892045] usb 1-5: new high speed USB device using ehci_hcd and address 4
[75622.090936] scsi4 : SCSI emulation for USB Mass Storage devices
[80334.113665] usb 1-5: USB disconnect, address 4
[82427.681151] usb 1-5: new high speed USB device using ehci_hcd and address 5
[82428.000929] scsi5 : SCSI emulation for USB Mass Storage devices

jeff@jeff-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa5bfa5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8d55133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7296    58597087+   f  W95 Ext'd (LBA)
/dev/sdb5               2        7296    58597056    b  W95 FAT32[/INDENT]


How do I interpret this and find the location of my USB device?

Thanks!

It's sdb

---

### Post by abelianjeff on 2009-01-12
> **theozzlives said:**
> It's sdb

Thanks! Now, I'm fsck is not running. Here is what I get:

[INDENT]jeff@jeff-laptop:~$ sudo fsck -vp /dev/sdb
fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/INDENT]

---

### Post by abelianjeff on 2009-01-16
*bump*

Does anybody have any ideas? To recap, lsusb is recognizing the hard drive's presence, but I don't know what to do from there. Nautilus et al. do not recognize my drive; it is invisible on Ubuntu. Perhaps even more depressingly, it IS recognized on a Windows machine. Any and all help is appreciated. (Please be explicit with your instructions, because I'm still rather new to this. I appreciate everyone's help, but I honestly don't know how to interpret something like "It's sdb." -- elaboration would be very helpful!)

---

### Post by abelianjeff on 2009-01-17
I followed the instructions here:[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

This allowed me to mount the hard drive. However, the files all appear corrupted and locked.

My drive is formatted FAT32.

Is there a way to reformat the harddrive with ext3? Would this even help the issue?

Ideally I would like to be able to simply plug my hard drive in and use it.

---

### Post by abelianjeff on 2009-01-17
I was able to fix the problem with a lot of brute force and the use of gparted. Thanks everyone.

---

### Post by dcstar on 2009-01-17
> **abelianjeff said:**
> Thanks! Now, I'm fsck is not running. Here is what I get:

[INDENT]jeff@jeff-laptop:~$ sudo fsck -vp /dev/sdb
fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/INDENT]

No, "sdb" is the device, "sdb1" or sdb2" are the partitions on it that you have to do the fsck on:

```
fsck -y /dev/sdb1
fsck -y /dev/sdb2
```

---


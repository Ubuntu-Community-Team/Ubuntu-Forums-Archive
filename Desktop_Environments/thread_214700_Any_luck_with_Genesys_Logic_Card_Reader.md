---
title: "Any luck with Genesys Logic Card Reader"
date: 2006-07-13
forum: Desktop Environments
---

### Post by rscarriere on 2006-07-13
I have a multi-card reader installed in my desktop system.  Currently only the CF (compact flash) works, but I am unable to get the SD cards to work (these are the only two I need).  Has anyone else had sucess with this reader?

Not sure what output would help to solve the problem - I've attached lsusb + dmesg below.  

lsusb output:
Bus 001 Device 004: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader

dmesg:
[   32.503169] usb 2-1.2: new full speed USB device using ohci_hcd and address 5
[   35.599849]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[   35.599858]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   35.606223] sd 4:0:0:0: Attached scsi removable disk sdc
[   35.607824]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[   35.607831]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   35.614194] sd 4:0:0:1: Attached scsi removable disk sdd
[   35.615808]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[   35.615814]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   35.622185] sd 4:0:0:2: Attached scsi removable disk sde
[   35.624038]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[   35.624047]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   35.630171] sd 4:0:0:3: Attached scsi removable disk sdf
[   35.630407] usb-storage: device scan complete

---

### Post by dbachran on 2007-12-03
I have the same issue, with Kubuntu 7.04 (Feisty Fawn). MMC cards work just fine, but SD cards don't. May be an issue with kernel drivers for SD...

But, running 'fdisk -l' with the SD card inserted shows the card just fine, so the kernel seems to know about it:

```
$ fdisk -l

Disk /dev/sdd: 2032 MB, 2032664576 bytes
41 heads, 40 sectors/track, 2420 cylinders
Units = cylinders of 1640 * 512 = 839680 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2421     1984992+   6  FAT16

```

Note: I've read somewhere else on the web that the kernel modules "usb_storage" and "sd_mod" play an important role here. Those two modules seem to be loaded by default here.

From there on, the sd card was just a "mount" away:

```
$ sudo mount /dev/sdd1 /mnt
$ df /mnt/
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdd1              1984704        32   1984672   1% /mnt

```

Of course, it still doesn't pop up in KDEs automout dialog, which I'll check once I'll have some more time...

ciao, daniel :-)

PS: I've included this post here in case somebody else may also have similar issues.

---


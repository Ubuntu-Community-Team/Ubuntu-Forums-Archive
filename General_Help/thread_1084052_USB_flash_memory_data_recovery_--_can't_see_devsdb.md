---
title: "USB flash memory data recovery -- can't see /dev/sdb"
date: 2009-03-01
forum: General Help
---

### Post by semi-newbie on 2009-03-01
Hello,

I have been attempting to try to use programs like gddrescue to access my 64Mb flash drive to recover some data (the flash drive has been corrupted -- I am guessing that MacOS X crapped all over the boot record when I tried to drag and drop a file onto it!).  Unfortunately, my computer won't let me access /dev/sdb (even as root).  For instance, cfdisk /dev/sdb yields "FATAL ERROR: Cannot open disk drive".

I am running an apt-get-updated version of Ubuntu 8.10.  Here's what shows up in /var/log/messages when I plug the USB stick into a port:

usb 7-2: new high speed USB device using ehci_hcd and address 3
usb 7-2: configuration #1 chosen from 1 choice
usbcore: registered new interface driver libusual
Initializing USB Mass Storage driver...
scsi6 : SCSI emulation for USB Mass Storage devices
uisbcore: registered new interface driver usb-storage
USB Mass Storage supoort registered.
scsi 6:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
sd 6:0:0:0: [sdb] Attached SCSI removable disk
sd 6:0:0:0: Attached scsi generic sg2 type 0

I tried to work around my inability to access /dev/sdb (as root) by using "raw" to make a raw device that points to /dev/sdb2 as per the info pages within gddrescue, but I got a missing "/dev/rawctl" error, and when I looked for help on that I found that it was obsolete.

Help, please!

---


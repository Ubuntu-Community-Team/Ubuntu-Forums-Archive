---
title: "can't rename usb 1gb stick"
date: 2006-01-21
forum: Desktop Environments
---

### Post by yigal.weinstein on 2006-01-21
I have a usb storage device that loads automatically when inserted into a usb drive.  The problem, although small, is that it is called *991.5MB Removable Storage*.  I want to it to have a good name, like *my_name usb storage* etc..  

The question I have is:
_Is there an easy way to rename the device so that every time it automounts it uses the name I changed it to _ (at least in Breezy)?

The part of the *dmesg* that seams to relate to this device is,

[FONT="System"][4294678.335000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[4294679.703000] SCSI subsystem initialized
[4294679.704000] Initializing USB Mass Storage driver...
[4294679.705000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294679.705000] usb-storage: device found at 2
[4294679.705000] usb-storage: waiting for device to settle before scanning
[4294679.705000] usbcore: registered new driver usb-storage
[4294679.705000] USB Mass Storage support registered.
[/FONT]

my /etc/fstab is for a normal computer with HD with the exception of an NTFS Windows partition mounted.

---

### Post by meonkeys on 2008-03-31
See here: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Related post: [http://ubuntuforums.org/showthread.php?t=123157](http://ubuntuforums.org/showthread.php?t=123157)

Same thing, by a blogger: [http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

---


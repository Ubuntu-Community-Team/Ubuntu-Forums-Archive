---
title: "determing fs type of USB HD"
date: 2008-07-03
forum: Desktop Environments
---

### Post by bobdobbs on 2008-07-03
Hi all.

I'm using Heron.

I'm recovering the contents of an not-so-old hard drive.
I've got a set of cables that power the drive and connect it to a USB port, so that my desktop should just see a USB storage device.

When I powered up the device, it seems to behave ok. The lights go on and the disk whirs.

But no new icon appears on the gnome desktop, so it's not mounting automatically.

Dmesg tells me that a device has been found:

> [22579.981184] usb 4-2: new high speed USB device using ehci_hcd and address 5
[22580.113969] usb 4-2: configuration #1 chosen from 1 choice
[22580.164536] usbcore: registered new interface driver libusual
[22580.175987] Initializing USB Mass Storage driver...
[22580.176741] scsi6 : SCSI emulation for USB Mass Storage devices
[22580.176870] usbcore: registered new interface driver usb-storage
[22580.176873] USB Mass Storage support registered.
[22580.176946] usb-storage: device found at 5
[22580.176947] usb-storage: waiting for device to settle before scanning
[22585.172178] usb-storage: device scan complete
[22585.172917] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[22585.178578] sd 6:0:0:0: [sdb] Attached SCSI disk
[22585.178611] sd 6:0:0:0: Attached scsi generic sg2 type 0



If I read that right, then the device should be at /dev/sdb.

So, I try:
mount /dev/sdb /USB-drive.

I get:
mount: you must specify the filesystem type

Darn! I can't remember the filesystem type!

How do I determine the fs type? Is there a way to figure out the fs type once I've got the drive physically hooked up?

---

### Post by ibutho on 2008-07-03
Try using the "blkid" command.

---

### Post by bobdobbs on 2008-07-03
Hi.

blkid gives me:
/dev/sda1: UUID="6dd4547e-3991-48a1-8f65-8360b21e4f3e" TYPE="ext3" 
/dev/sda2: UUID="c20abb0d-7141-48a9-be81-5ab3d0026e15" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="71655d2b-148a-4b59-aba3-dfb5d8176a2b" 
/dev/sda4: UUID="60589a74-3df0-4638-8c83-cee85bd4aeaf" TYPE="ext3" 

These devices are the existing partitions of the partitions on my resident hard drive. 

I've tried this with all the hard drives that I've got sitting here.

Does this mean that my system isn't finding any of the hard drives?
I don't believe that all four of them are damaged. The odds make that unlikely.

According to dmesg the drives get found. But they seem to be invisible to blkid.

What on earth is going on here? And how do I get my data back?

---

### Post by p_quarles on 2008-07-03
Run:
```
sudo fdisk -l
```
Or, if you prefer a graphical representation, you can install gparted and run that. These (both partition managers/editors) will be able to examine and identify details on all attached storage devices.

---

### Post by bobdobbs on 2008-07-03
> **p_quarles said:**
> Run:
```
sudo fdisk -l
```
Or, if you prefer a graphical representation, you can install gparted and run that. These (both partition managers/editors) will be able to examine and identify details on all attached storage devices.


I've found a workaround for the moment.
My laptop picks up the hard drives with the same USB adaptor cable.
So I'm using gftp to transfer the files via SSH.

It's a solution for recovering the data, but of course it leaves an problem that I'm going to have to solve in the future.

Thanks for the input, guys.

---


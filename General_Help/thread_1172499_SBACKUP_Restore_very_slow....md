---
title: "SBACKUP Restore very slow..."
date: 2009-05-28
forum: General Help
---

### Post by rompstar on 2009-05-28
So I have been testing SBACKUP, I set it up correctly and it backs up to a external USB drive, I have 9.04 Ubuntu Server with Desktop installed.

But when I do the restore, even when I select to restore 1 file, that is very small under 1MB, it takes over an hour, why ?

And the GUI seems to like go blank and lock up.  I just leave it alone and eventually whatever it was doing, it's done.

---

### Post by upbeat.linux on 2009-05-28
Are backups or purges running when you attempt to restore the file? Is there anything else reading-from/writing-to the disk? Are you restoring data to the USB drive?

Try running:

```
dmesg
```

and looking for messages related to USB.

Have you tried manually extracting the archive to see if there are errors?

How is the usb drive formated: NTFS, FAT, FAT32, ext3, reiser, etc?

---

### Post by rompstar on 2009-05-28
my USB Drive is ext3, here is some stuff from dmesg about USB 

I don't really know how to manually extract the backup data, since this is a fresh install, I have not setup a backup, so I don't think there is anything else that is operating on it, just doing the restore 

[    2.754045] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    2.990035] usb 1-1: configuration #1 chosen from 1 choice
[    2.998462] usbcore: registered new interface driver hiddev
[    3.008239] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /devices/pci0000:00/0000:00:06.0/0000:01:00.0/usb1/1-1/1-1:1.0/input/input4
[    3.022557] generic-usb 0003:045E:0029.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:01:00.0-1/input0
[    3.022578] usbcore: registered new interface driver usbhid
[    3.022581] usbhid: v2.6:USB HID core driver
[    3.170025] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    3.393933] usb 2-1: configuration #1 chosen from 1 choice
[    3.396871] hub 2-1:1.0: USB hub found
[    3.399841] hub 2-1:1.0: 4 ports detected
[    3.701795] usb 2-1.1: new full speed USB device using ohci_hcd and address 3
[    3.847818] usb 2-1.1: configuration #1 chosen from 1 choice
[    3.854895] Initializing USB Mass Storage driver...
[    3.855035] scsi3 : SCSI emulation for USB Mass Storage devices
[    3.855127] usbcore: registered new interface driver usb-storage
[    3.855130] USB Mass Storage support registered.
[    3.855249] usb-storage: device found at 3
[    3.855251] usb-storage: waiting for device to settle before scanning
[    3.931759] usb 2-1.2: new full speed USB device using ohci_hcd and address 4
[    4.059818] usb 2-1.2: configuration #1 chosen from 1 choice
[    4.063290] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.063387] usb-storage: device found at 4
[    4.063389] usb-storage: waiting for device to settle before scanning
[    8.851997] usb-storage: device scan complete

---

### Post by legendbb on 2011-06-14
Just to add my experience in 2011.

I used bz2 for compression, and my full back up is about 20G.

It takes extreme long to restore a single file, and cpu is 100% at bzip2, already one hour. Don't know how much longer it still gonna take; wish it's not dead. And there is no backup running and continuous access to the backup disk.

Really concerned.

---

### Post by psusi on 2011-06-14
AFAIK, sbackup saves to a .tar.bz2, so to extract a file from the middle or end of the archive requires that everything before it be read and decompressed first.

---

### Post by akaihola on 2012-01-20
> **psusi said:**
> AFAIK, sbackup saves to a .tar.bz2, so to extract a file from the middle or end of the archive requires that everything before it be read and decompressed first.

Not compressing doesn't help much either if the data is on a USB disk, since all the preceding data still needs to be read in, and that takes time on USB.

---


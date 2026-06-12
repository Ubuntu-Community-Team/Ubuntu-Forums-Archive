---
title: "Cannot mount USB memory stick (Cruzer Micro 1GB)"
date: 2008-12-06
forum: General Help
---

### Post by Eyeless Blond on 2008-12-06
Hi, new Ubuntu user here, working from a brand new computer. I'm having a problem mounting my old USB memory stick to the new computer. When I try to open it in the file browser, it tells me there is no media in the drive. dmesg gives me:

[158492.232017] usb 6-6: new high speed USB device using ehci_hcd and address 3
[158492.366397] usb 6-6: configuration #1 chosen from 1 choice
[158492.387123] scsi7 : SCSI emulation for USB Mass Storage devices
[158492.388349] usb-storage: device found at 3
[158492.388356] usb-storage: waiting for device to settle before scanning
[158497.388205] usb-storage: device scan complete
[158497.388806] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[158497.389295] scsi 7:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[158497.391129] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[158497.391411] sd 7:0:0:0: Attached scsi generic sg2 type 0
[158497.394789] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[158497.394883] sr 7:0:0:1: Attached scsi CD-ROM sr1
[158497.394983] sr 7:0:0:1: Attached scsi generic sg3 type 5
aaron@Eyes:/$ 

How do I fix this? Or can I? The stick is an old 1GB Cruzer Micro, which I understand has reliability problems; did mine just give up the ghost?

---

### Post by dcstar on 2008-12-06
> **Eyeless Blond said:**
> Hi, new Ubuntu user here, working from a brand new computer. I'm having a problem mounting my old USB memory stick to the new computer. When I try to open it in the file browser, it tells me there is no media in the drive. dmesg gives me:

[158492.232017] usb 6-6: new high speed USB device using ehci_hcd and address 3
[158492.366397] usb 6-6: configuration #1 chosen from 1 choice
[158492.387123] scsi7 : SCSI emulation for USB Mass Storage devices
[158492.388349] usb-storage: device found at 3
[158492.388356] usb-storage: waiting for device to settle before scanning
[158497.388205] usb-storage: device scan complete
[158497.388806] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[158497.389295] scsi 7:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[158497.391129] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[158497.391411] sd 7:0:0:0: Attached scsi generic sg2 type 0
[158497.394789] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[158497.394883] sr 7:0:0:1: Attached scsi CD-ROM sr1
[158497.394983] sr 7:0:0:1: Attached scsi generic sg3 type 5
aaron@Eyes:/$ 

How do I fix this? Or can I? The stick is an old 1GB Cruzer Micro, which I understand has reliability problems; did mine just give up the ghost?

Install the **gparted** package, and then use it to see if there is a formatted partition that Linux can detect on the drive.

---

### Post by Eyeless Blond on 2008-12-07
> **dcstar said:**
> Install the **gparted** package, and then use it to see if there is a formatted partition that Linux can detect on the drive.

Nothing, just my hard drive partitions.

Hrm, here's something weird. gnome-device-manager is telling me that i have a mass storage device with a device file of /dev/sdb, but "sudo fdisk /dev/sdb -l" gives me nothing, not even an error message.

---

### Post by Eyeless Blond on 2008-12-07
Oh, teriffic, I just remembered I used the U3 software to encrypt everything on the drive. I'm guessing that might be the reason nothing works? If so, there's no way for me to get ahold of my data, is there?

---

### Post by falcon61102 on 2008-12-07
When you encrypted the drive did you encrypt the entire file system or just all the files on it?  

You may be able to download the U3 program from their website and use it to decrypt the drive.  I'm not sure about U3's Linux compatibility so if you have a dual-boot or another computer with windows, you may want to use that.  Or you could attempt to use wine, though I have no idea if that would work.

---

### Post by Eyeless Blond on 2008-12-07
*sigh* The entire file system.

As far as I can tell from cruising the net, it would seem that U3 is completely incompatible with Linux. Apparently I can't even remove it without windows. Oh well; guess I'll just have to borrow a computer and remove the cruft... and buy a new USB stick.

---

### Post by falcon61102 on 2008-12-07
If you can decrypt the drive on another computer, there is an option to remove U3 from the drive complete so that it can be used on any system.  That will save you from having to buy another drive.

---


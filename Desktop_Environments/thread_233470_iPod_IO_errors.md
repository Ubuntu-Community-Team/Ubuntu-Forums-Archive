---
title: "iPod I/O errors"
date: 2006-08-10
forum: Desktop Environments
---

### Post by SirKillalot on 2006-08-10
Hello,
I bought an iPod video few weeks ago but I can't really access it with Linux. It seems that the FAT32 driver fails writing on the iPod. Sometimes I can write a few Mb and then the device get mounted read-only or I get I/O errors like the following:

```
[17186811.528000] usb 4-6: new high speed USB device using ehci_hcd and address 6
[17186811.660000] usb 4-6: configuration #1 chosen from 2 choices
[17186811.660000] scsi1 : SCSI emulation for USB Mass Storage devices
[17186811.660000] usb-storage: device found at 6
[17186811.660000] usb-storage: waiting for device to settle before scanning
[17186816.660000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17186816.660000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17186816.660000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[17186816.664000] sda: Write Protect is off
[17186816.664000] sda: Mode Sense: 6c 00 00 08
[17186816.664000] sda: assuming drive cache: write through
[17186816.664000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[17186816.664000] sda: Write Protect is off
[17186816.664000] sda: Mode Sense: 6c 00 00 08
[17186816.664000] sda: assuming drive cache: write through
[17186816.664000]  sda: sda1 sda2
[17186816.676000] sd 1:0:0:0: Attached scsi removable disk sda
[17186816.676000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17186816.676000] usb-storage: device scan complete
[17186986.244000] usb 4-6: reset high speed USB device using ehci_hcd and address 6
[17186996.488000] usb 4-6: reset high speed USB device using ehci_hcd and address 6
[17187012.832000] usb 4-6: reset high speed USB device using ehci_hcd and address 6
[17187013.080000] usb 4-6: reset high speed USB device using ehci_hcd and address 6
[17187023.324000] usb 4-6: reset high speed USB device using ehci_hcd and address 6
[17187023.456000] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
[17187023.456000] sd 1:0:0:0: SCSI error: return code = 0x50000
[17187023.456000] end_request: I/O error, dev sda, sector 222250
[17187023.456000] printk: 802 messages suppressed.
[17187023.456000] Buffer I/O error on device sda2, logical block 61600
[17187023.456000] lost page write due to I/O error on sda2
[17187023.456000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.456000] Buffer I/O error on device sda2, logical block 61601
[17187023.456000] lost page write due to I/O error on sda2
[17187023.456000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.456000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.456000] sd 1:0:0:0: SCSI error: return code = 0x10000
[17187023.456000] end_request: I/O error, dev sda, sector 274720
[17187023.456000] Buffer I/O error on device sda2, logical block 114070
[17187023.456000] lost page write due to I/O error on sda2
[17187023.456000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.456000] FAT: FAT read failed (blocknr 4583)
[17187023.460000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.460000] Buffer I/O error on device sda2, logical block 4772670
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] Buffer I/O error on device sda2, logical block 4772671
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.460000] Buffer I/O error on device sda2, logical block 4774214
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] Buffer I/O error on device sda2, logical block 4774215
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] Buffer I/O error on device sda2, logical block 4774216
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] Buffer I/O error on device sda2, logical block 4774217
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] Buffer I/O error on device sda2, logical block 4774218
[17187023.460000] lost page write due to I/O error on sda2
[17187023.460000] sd 1:0:0:0: rejecting I/O to offline device
[17187023.460000] sd 1:0:0:0: rejecting I/O to offline device
[17187031.136000] sd 1:0:0:0: rejecting I/O to offline device
[17187031.136000] printk: 61 messages suppressed.
[17187031.136000] Buffer I/O error on device sda2, logical block 1
[17187031.136000] lost page write due to I/O error on sda2
[17187031.136000] sd 1:0:0:0: rejecting I/O to offline device
[17187031.136000] sd 1:0:0:0: rejecting I/O to offline device
caglar@nerd:~$

```

Since I updated to Dapper my USB seems to be a bit strange. When I try to copy something on an USB device the kernel thinks that it is VERY fast. It says that the transfer is done after a few seconds although the transfer still goes on which I can see in the CPU usage and the storage device. Maybe it "works to fast" for the driver. Therefore I wonder, if I can set an operating speed for the USB devices anywhere.
Sincerly
Sirk

---

### Post by mcduck on 2006-08-10
It seems that you ave same problem with your iPod that I have. As far as I know it's because the USB controller in iPod reports the hard disk to be a bit bigger than it really is. (Thanks, Apple, for your great hardware :P) So when you system tries to access those non-existing sectors on the disk problems start. I've made a bug report about this, as everything worked fine in Hoary and Breezy, but this far nobody seems to know why some iPod's have this problem now when it was already working in earlier versions.

I had my iPod working fine with Dapper for a while by recompiling kernel and disabling EFI-partition support. But even that doesn't seem to work any more. 

What comes to other USB devices, that's just normal. Disk writes are buffered in Linux and handled in background, and that's why it's important to eject/unmount external medias correctly.

---

### Post by SirKillalot on 2006-08-15
Hello,
its good to hear that I'm not the only person who has this kind of problem. I also tried to repair the filesystem with the fsck tool, but that doesn't really work for me. I can transfer some megabytes more than I could normally do but in the end I get an error. No way...
regards

---

### Post by shanepardue on 2006-09-04
same here..anyone find a solution?

---


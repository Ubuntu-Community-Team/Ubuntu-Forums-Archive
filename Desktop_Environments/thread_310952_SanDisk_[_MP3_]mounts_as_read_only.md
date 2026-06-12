---
title: "SanDisk [ MP3 ]mounts as read only"
date: 2006-12-02
forum: Desktop Environments
---

### Post by johnbl on 2006-12-02
Haing a ' few ' problems with getting my SanDisk player to mount with usable permissions. 

dmesg below shows - or appears to - that it multi auto mounts;
Across the top of the screen 13 [ thirteen ] boxes appear - that can't be right surely, one I could understand and would seem correct but 13!

There is no entry in fstab for Sansa e250 - I tried that and untill it was removed the thing wouldn't mount at all!

Could it be the driver message that's highlighting the problem, but where would I get it and bus_method? Any ideas out there as to what that means?

Appears this MP3 as a read only mount is a common 'ish ' problem but can't see where anyone having solved it has posted a how too. That possible means the answer is so obvious it causes embarresment, so embarress me, please, I'm big!

Any ideas most appreciated.

John

](*,) 
[17181756.464000] Initializing USB Mass Storage driver...
[17181756.464000] scsi0 : SCSI emulation for USB Mass Storage devices
[17181756.464000] usb-storage: device found at 5
[17181756.464000] usb-storage: waiting for device to settle before scanning
[17181756.464000] usbcore: registered new driver usb-storage
[17181756.464000] USB Mass Storage support registered.
[17181761.468000]   Vendor: SanDisk   Model: Sansa e250        Rev:
[17181761.468000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17181761.472000]   Vendor: SanDisk   Model: Sansa e250        Rev:
[17181761.472000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17181761.480000] usb-storage: device scan complete
[17181761.676000] Driver 'sd' needs updating - please use bus_type methods
[17181761.684000] SCSI device sda: 3926016 512-byte hdwr sectors (2010 MB)
[17181761.688000] sda: Write Protect is off
[17181761.688000] sda: Mode Sense: 45 00 00 00
[17181761.688000] sda: assuming drive cache: write through
[17181761.772000] SCSI device sda: 3926016 512-byte hdwr sectors (2010 MB)
[17181761.776000] sda: Write Protect is off
[17181761.776000] sda: Mode Sense: 45 00 00 00
[17181761.776000] sda: assuming drive cache: write through
[17181761.780000]  sda: sda1 sda2
[17181761.848000] sd 0:0:0:0: Attached scsi removable disk sda
[17181761.920000] sd 0:0:0:1: Attached scsi removable disk sdb
[17181761.944000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17181761.944000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[17181763.288000] FAT: utf8 is not a recommended IO charset for FAT filesystems,  filesystem will be case sensitive!

---


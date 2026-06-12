---
title: "Just Cannot use iPod :("
date: 2006-09-11
forum: Desktop Environments
---

### Post by SirKillalot on 2006-09-11
This is what I get (dmesg) when I try to transfer a song from amarok to my ipod after I did a full reset and recover with apple update tool.
Is there ANYTHING I can do? Is it a kernel bug? Is there any hope?

```

[17180196.768000] SCSI subsystem initialized
[17180196.780000] Initializing USB Mass Storage driver...
[17180196.780000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180196.780000] usb-storage: device found at 4
[17180196.780000] usb-storage: waiting for device to settle before scanning
[17180196.780000] usbcore: registered new driver usb-storage
[17180196.780000] USB Mass Storage support registered.
[17180201.780000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17180201.780000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17180201.792000] usb-storage: device scan complete
[17180201.820000] Driver 'sd' needs updating - please use bus_type methods
[17180201.824000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[17180201.824000] sda: Write Protect is off
[17180201.824000] sda: Mode Sense: 6c 00 00 08
[17180201.824000] sda: assuming drive cache: write through
[17180201.832000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[17180201.832000] sda: Write Protect is off
[17180201.832000] sda: Mode Sense: 6c 00 00 08
[17180201.832000] sda: assuming drive cache: write through
[17180201.832000]  sda: sda1 sda2
[17180201.848000] sd 0:0:0:0: Attached scsi removable disk sda
[17180201.860000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180202.584000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180367.916000] usb 4-6: reset high speed USB device using ehci_hcd and address 4
[17180378.160000] usb 4-6: reset high speed USB device using ehci_hcd and address 4
[17180394.504000] usb 4-6: reset high speed USB device using ehci_hcd and address 4
[17180394.768000] usb 4-6: reset high speed USB device using ehci_hcd and address 4
[17180405.012000] usb 4-6: reset high speed USB device using ehci_hcd and address 4
[17180405.144000] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[17180405.144000] sd 0:0:0:0: SCSI error: return code = 0x50000
[17180405.144000] end_request: I/O error, dev sda, sector 311872
[17180405.144000] Buffer I/O error on device sda2, logical block 151222
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] Buffer I/O error on device sda2, logical block 151223
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151224
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151225
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151226
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151227
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151228
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151229
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151230
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] Buffer I/O error on device sda2, logical block 151231
[17180405.144000] lost page write due to I/O error on sda2
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.144000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.156000] sd 0:0:0:0: SCSI error: return code = 0x10000
[17180405.156000] end_request: I/O error, dev sda, sector 312000
[17180405.156000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] FAT: Directory bread(block 114174) failed
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] FAT: Directory bread(block 114174) failed
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.192000] FAT: Directory bread(block 114174) failed
[17180405.192000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.196000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.196000] FAT: Directory bread(block 114174) failed
[17180405.196000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.196000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.196000] FAT: Directory bread(block 114174) failed
[17180405.196000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.196000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.196000] FAT: Directory bread(block 114174) failed
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] FAT: Directory bread(block 114174) failed
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] FAT: Directory bread(block 114174) failed
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] FAT: Directory bread(block 114174) failed
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] FAT: FAT read failed (blocknr 113)
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] FAT: bread failed in fat_clusters_flush
[17180405.200000] sd 0:0:0:0: rejecting I/O to offline device
[17180405.200000] FAT: unable to read inode block for updating (i_pos 1825253)
[17180405.204000] sd 0:0:0:0: rejecting I/O to offline device
```

---

### Post by elvis on 2006-09-11
Getting the same error here.  No idea what's causing it.  The iPod works fine in other operating systems with iTunes.

Happens under 2.6.15-26-686 and 2.6.15-26-386 with the same dmesg output as above.  Any help/tips/ideas would be appreciated.

---

### Post by SirKillalot on 2006-09-13
Seems that I'll never be able to use my lovely iPod :(

---

### Post by brucevangeorge on 2006-09-15
What is this: Driver 'sd' needs updating business?

I get the same thing....

---


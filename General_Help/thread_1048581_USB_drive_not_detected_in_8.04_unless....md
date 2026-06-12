---
title: "USB drive not detected in 8.04 unless..."
date: 2009-01-23
forum: General Help
---

### Post by levesque on 2009-01-23
I'm not sure what section I should post this in so any suggestions on that would be appreciated.

I have a 80g USB (fat32) drive and everything worked with Dapper but since I upgraded to 8.04 during boot I get this:

[ 3241.567070] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[ 3271.898443] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[ 3302.225819] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[ 3302.461239] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3302.461250] end_request: I/O error, dev sdb, sector 0
[ 3302.461255] Buffer I/O error on device sdb, logical block 0

if I do nothing it will eventually finish booting but no USB drive. Once booting is finished I can replug it, or plug it in if it wasn't, and it's detected:

[18679.853500] usb 4-4: new high speed USB device using ehci_hcd and address 3
[18679.985452] usb 4-4: configuration #1 chosen from 1 choice
[18679.986374] scsi5 : SCSI emulation for USB Mass Storage devices
[18679.986802] usb-storage: device found at 3
[18679.986808] usb-storage: waiting for device to settle before scanning
[18684.981870] usb-storage: device scan complete
[18684.983730] scsi 5:0:0:0: Direct-Access     ST94813A                  3.04 PQ: 0 ANSI: 0 CCS
[18684.985226] sd 5:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[18684.990360] sd 5:0:0:0: [sdb] Write Protect is off
[18684.990369] sd 5:0:0:0: [sdb] Mode Sense: 00 14 00 00
[18684.990373] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[18684.991584] sd 5:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[18684.992208] sd 5:0:0:0: [sdb] Write Protect is off
[18684.992214] sd 5:0:0:0: [sdb] Mode Sense: 00 14 00 00
[18684.992217] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[18684.992225]  sdb: sdb1
[18685.005230] sd 5:0:0:0: [sdb] Attached SCSI disk
[18685.005304] sd 5:0:0:0: Attached scsi generic sg2 type 0

(but I still have to open it once by double clicking on the icon if I want sbackup to be able to access it automatically)

Any suggestions what I might try? 

Marc

---


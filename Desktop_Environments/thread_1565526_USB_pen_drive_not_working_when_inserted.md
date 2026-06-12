---
title: "USB pen drive not working when inserted"
date: 2010-09-01
forum: Desktop Environments
---

### Post by mickwombat on 2010-09-01
Hi,
Firstly, I'm an experienced Ubuntu user and have a problem with a certain USB pen drive.  It doesn't seem to be recognised in Ubuntu and I can't browse it.  Other USB sticks *do* work and this drive works in Windows.

```
mick@mick-laptop:/media$ dmesg | tail -20
[ 2494.011373] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2494.011378] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[ 2494.011389] end_request: I/O error, dev sdb, sector 8
[ 2494.011396] Buffer I/O error on device sdb, logical block 1
[ 2498.396062] usb 1-1: new high speed USB device using ehci_hcd and address 34
[ 2498.529940] usb 1-1: configuration #1 chosen from 1 choice
[ 2498.550645] scsi4 : SCSI emulation for USB Mass Storage devices
[ 2498.553654] usb-storage: device found at 34
[ 2498.553658] usb-storage: waiting for device to settle before scanning
[ 2503.554186] usb-storage: device scan complete
[ 2503.554718] scsi 4:0:0:0: Direct-Access     Generic  USB Flash Drive  1.00 PQ: 0 ANSI: 2
[ 2503.558184] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2503.562556] sd 4:0:0:0: [sdb] 2064384 512-byte logical blocks: (1.05 GB/1008 MiB)
[ 2503.564367] sd 4:0:0:0: [sdb] Write Protect is off
[ 2503.564375] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2503.564379] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2503.575201] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2503.575212]  sdb: sdb1
[ 2503.597833] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2503.597871] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

When I do an #fdisk -l, it just hangs and doesn't list anything for this drive.  Opening GParted also hangs until I remove the stick.

Any ideas on whats up with this thing?

Thanks

---

### Post by mickwombat on 2010-09-28
Anyone?

---

### Post by linux-hack on 2010-09-28
Did you unplug it safely from windows ? sometimes if you unplug the usb key from a windows system without disconcerting it safely, ubuntu will not be able to read it.

---


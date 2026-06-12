---
title: "Weird nautilus restarts on insertion of disk/USB"
date: 2009-01-02
forum: General Help
---

### Post by isecore on 2009-01-02
This is a rather strange (and irritating) phenomenon that has popped up in the last few days after applying updates.

Nowadays when I insert a USB thumbdrive (or a CD/DVD) it seems that Nautilus restarts. Any open Nautilus-windows gets killed, any background process (i.e. copying files or whatever) gets killed and the desktop blinks and hiccups then reloads.

Anyone have any idea as to why this is happening and how to fix it?

---

### Post by dcstar on 2009-01-02
> **isecore said:**
> This is a rather strange (and irritating) phenomenon that has popped up in the last few days after applying updates.

Nowadays when I insert a USB thumbdrive (or a CD/DVD) it seems that Nautilus restarts. Any open Nautilus-windows gets killed, any background process (i.e. copying files or whatever) gets killed and the desktop blinks and hiccups then reloads.

Anyone have any idea as to why this is happening and how to fix it?

If you look at the output of the dmesg command you may get some more info.

---

### Post by isecore on 2009-01-02
I checked that, but dozens of messages identical to this one didn't really give me any clue.

```
[29262.918439] usb 6-5: reset high speed USB device using ehci_hcd and address 7
```

---

### Post by dcstar on 2009-01-02
> **isecore said:**
> I checked that, but dozens of messages identical to this one didn't really give me any clue.

```
[29262.918439] usb 6-5: reset high speed USB device using ehci_hcd and address 7
```

Boot off the previous kernel and see if it still happens.

---

### Post by isecore on 2009-01-03
> **dcstar said:**
> Boot off the previous kernel and see if it still happens.

Tried that. Made no difference. Not that I really expected it too either.

After some experimenting, here's what happens when I insert a USB thumbdrive:

```
[  200.621529] usb 1-9: new high speed USB device using ehci_hcd and address 13
[  200.756105] usb 1-9: configuration #1 chosen from 1 choice
[  200.758300] scsi15 : SCSI emulation for USB Mass Storage devices
[  200.759977] usb-storage: device found at 13
[  200.759987] usb-storage: waiting for device to settle before scanning
[  200.770773] nautilus[7514]: segfault at 31 ip 0000000000000031 sp 00007fffcc355db8 error 14 in nautilus[400000+159000]
[  205.760792] usb-storage: device scan complete
[  205.761360] scsi 15:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  205.762460] sd 15:0:0:0: [sdh] 7888896 512-byte hardware sectors (4039 MB)
[  205.763086] sd 15:0:0:0: [sdh] Write Protect is off
[  205.763092] sd 15:0:0:0: [sdh] Mode Sense: 23 00 00 00
[  205.763096] sd 15:0:0:0: [sdh] Assuming drive cache: write through
[  205.764709] sd 15:0:0:0: [sdh] 7888896 512-byte hardware sectors (4039 MB)
[  205.765331] sd 15:0:0:0: [sdh] Write Protect is off
[  205.765335] sd 15:0:0:0: [sdh] Mode Sense: 23 00 00 00
[  205.765338] sd 15:0:0:0: [sdh] Assuming drive cache: write through
[  205.765345]  sdh:<6>nautilus[7975]: segfault at 31 ip 0000000000000031 sp 00007fffbe4293c8 error 14 in nautilus[400000+159000]
[  205.883447]  sdh1
[  205.883670] sd 15:0:0:0: [sdh] Attached SCSI removable disk
[  205.883864] sd 15:0:0:0: Attached scsi generic sg8 type 0
[  206.235199] nautilus[8001]: segfault at 31 ip 0000000000000031 sp 00007fff275f8598 error 14 in nautilus[400000+159000]
[  372.864027] usb 1-5: reset high speed USB device using ehci_hcd and address 6
```

That's what's added to dmesg after I insert the device. Apparently something causes Nautilus to segfault. I'm thinking about filing a bug-report for this.

---

### Post by isecore on 2009-01-06
Filed a bug for it, y'all can find it here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/314081](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/314081)

---


---
title: "Using an .mp3 player with Ubuntu"
date: 2008-12-03
forum: General Help
---

### Post by DouglasT on 2008-12-03
Hey! I've recently started using Ubuntu. I have a portable .mp3 player that I'd like to manage with Ubuntu, but when I plug it in to my USB port, the system doesn't do anything. No error, just nothing. 

Any help? Thanks in advance!

---

### Post by ohzopants on 2008-12-03
Plug in your mp3 player and then run the command:
```

dmesg | tail

```

Post the output here and maybe I can help some more.

---

### Post by DouglasT on 2008-12-03
[ 1935.831186] sd 4:0:0:0: [sdb] Write Protect is off
[ 1935.831198] sd 4:0:0:0: [sdb] Mode Sense: 00 26 00 00
[ 1935.831204] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1935.832141]  sdb: sdb1
[ 1935.833945] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1935.834500] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 8810.892868] usb 5-8: USB disconnect, address 5
[ 8810.892877] usb 5-8.1: USB disconnect, address 6
[ 8821.372024] usb 5-8: new high speed USB device using ehci_hcd and address 7
[ 8821.526944] usb 5-8: configuration #1 chosen from 1 choice

---

### Post by ohzopants on 2008-12-04
That's weird.  It seems like Ubuntu is recognizing the USB device.

When you plug it in, does it show up under the "Places" menu?

---

### Post by DouglasT on 2008-12-07
> **ohzopants said:**
> That's weird.  It seems like Ubuntu is recognizing the USB device.

When you plug it in, does it show up under the "Places" menu?

Nope.

---


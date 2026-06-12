---
title: "External Hard Drive not being recognized"
date: 2009-08-13
forum: Desktop Environments
---

### Post by s3rvant on 2009-08-13
I have an external enclosure I use for pc repairs and I have a known good hard drive in it, formatted ntfs currently. When I connect the drive and try sudo fdisk -l the drive isn't listed. When I connect it and use dmesg | tail I get:

```
[ 8490.978371] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 8490.978993] sd 10:0:0:0: [sdh] 53464320 512-byte hardware sectors: (27.3 GB/25.4 GiB)
[ 8490.980123] sd 10:0:0:0: [sdh] Write Protect is off
[ 8490.980126] sd 10:0:0:0: [sdh] Mode Sense: 27 00 00 00
[ 8490.980127] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 8490.980130]  sdh:<6>usb 1-10: reset high speed USB device using ehci_hcd and address 4
[ 8509.708716] usb 1-10: reset high speed USB device using ehci_hcd and address 4
[ 8509.968265] usb 1-10: reset high speed USB device using ehci_hcd and address 4
[ 8521.112035] usb 1-6: reset high speed USB device using ehci_hcd and address 6
[ 8525.708589] usb 1-10: reset high speed USB device using ehci_hcd and address 4

```

Any help getting the drive to work would be much appreciated. In the mean time I'm going to dig around for another drive to test the enclosure with.

---


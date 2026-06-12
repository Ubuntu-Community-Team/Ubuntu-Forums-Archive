---
title: "Help Getting External HDD to Work (Won't Mount?)"
date: 2009-01-14
forum: General Help
---

### Post by Literati on 2009-01-14
I just bought an Acomdata external hard drive enclosure, and shoved a 500GB S-ATA drive in it. It's hooked up just as my working S-ATA drive is in my computer itself. However, it won't mount itself, and I can't figure out why. Here's the output of "tail /var/log/messages" from the moment I turn on the power.

```
Jan 14 14:14:57 Matt kernel: [ 1291.769018] usb 1-5: new high speed USB device using ehci_hcd and address 24
Jan 14 14:14:58 Matt kernel: [ 1292.315152] usb 1-5: new high speed USB device using ehci_hcd and address 25
Jan 14 14:14:58 Matt kernel: [ 1292.862233] usb 1-5: new high speed USB device using ehci_hcd and address 26
Jan 14 14:14:59 Matt kernel: [ 1293.377474] usb 1-5: new high speed USB device using ehci_hcd and address 27
Jan 14 14:19:57 Matt kernel: [ 1590.897429] usb 1-5: new high speed USB device using ehci_hcd and address 28
Jan 14 14:19:57 Matt kernel: [ 1591.031842] usb 1-5: configuration #1 chosen from 1 choice
Jan 14 14:19:57 Matt kernel: [ 1591.033835] scsi13 : SCSI emulation for USB Mass Storage devices
Jan 14 14:20:08 Matt kernel: [ 1602.626817] usb 1-5: reset high speed USB device using ehci_hcd and address 28
Jan 14 14:20:09 Matt kernel: [ 1603.171476] usb 1-5: reset high speed USB device using ehci_hcd and address 28
Jan 14 14:20:10 Matt kernel: [ 1603.718085] usb 1-5: reset high speed USB device using ehci_hcd and address 28
Jan 14 14:20:10 Matt kernel: [ 1604.236274] usb 1-5: reset high speed USB device using ehci_hcd and address 28
Jan 14 14:20:10 Matt kernel: [ 1604.643673] usb 1-5: USB disconnect, address 28
Jan 14 14:20:10 Matt kernel: [ 1604.643830] scsi 13:0:0:0: Device offlined - not ready after error recovery
Jan 14 14:20:11 Matt kernel: [ 1604.755448] usb 1-5: new high speed USB device using ehci_hcd and address 29
Jan 14 14:20:11 Matt kernel: [ 1605.300078] usb 1-5: new high speed USB device using ehci_hcd and address 30
Jan 14 14:20:12 Matt kernel: [ 1605.843219] usb 1-5: new high speed USB device using ehci_hcd and address 31
Jan 14 14:20:12 Matt kernel: [ 1606.360900] usb 1-5: new high speed USB device using ehci_hcd and address 32
```

How can there be errors if I've never done anything to the drive? And how can I fix it (fsck) if I can't mount it? :(

---

### Post by Titan8990 on 2009-01-14
Actually, you can only run fsck on disks that ARE NOT mounted.

Does the drive show up if you run the following command:


sudo fdisk -l

---

### Post by Literati on 2009-01-14
Hmm, now it seems to... I didn't try that command before though (And had to yank the USB and replug to get it to show) 

Let me try to partition it now... :)

EDIT: Yup, I must've put on my stupid cap this morning. :P Thank you very much for the help!

---


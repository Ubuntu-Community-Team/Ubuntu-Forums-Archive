---
title: "Ubuntu does not detect USB enclosure - IDE Hard drive"
date: 2009-05-28
forum: General Help
---

### Post by rold50 on 2009-05-28
I have a USB enclosure for my ATA hard drive.

When I plug it in to the USB, the drive is not showing up.

dmesg gives me this:

[ 5058.340032] usb 2-5: new high speed USB device using ehci_hcd and address 9
[ 5058.473669] usb 2-5: configuration #1 chosen from 1 choice
[ 5058.473977] scsi19 : SCSI emulation for USB Mass Storage devices
[ 5058.474071] usb-storage: device found at 9
[ 5058.474074] usb-storage: waiting for device to settle before scanning
[ 5063.472203] usb-storage: device scan complete
[ 5069.916012] usb 2-5: reset high speed USB device using ehci_hcd and address 9
[ 5075.916020] usb 2-5: reset high speed USB device using ehci_hcd and address 9
[ 5081.916023] usb 2-5: reset high speed USB device using ehci_hcd and address 9
[ 5087.916049] usb 2-5: reset high speed USB device using ehci_hcd and address 9


Any idea why the drive is not showing up?
fdisk -l does not show any drive too.
/proc/scsi/scsi does not show the drive too.

---


---
title: "USB Thumbdrive in Intrepid"
date: 2008-11-28
forum: Desktop Environments
---

### Post by cameron.maclean on 2008-11-28
I am having an issue with Intrepid Ibis and my 16GB ADATA Thumbdrive, currently I am connecting it through my HP Deskjet D4260, it has a single hub interface. 

The thumbdrive worked fine until I rebooted with the drive inserted. I have reinstalled Ubuntu from the CD, and still the drive doesn't work. 

It worked before the reboot with the drive inserted and now doesn't even on a fresh install. I'm pretty sure that it's something to do with the drive. 

I read somewhere that another user had luck with low level reformat of the drive, but I don't have another computer that I can do that on. 
I've tried the trick of disabling ehci_hcd and that does nothing.

Any help would be greatly appreciated

here is the dmesg output: 

[ 2262.148097] usb 5-4: new high speed USB device using ehci_hcd and address 2
[ 2262.287350] usb 5-4: configuration #1 chosen from 1 choice
[ 2262.289539] hub 5-4:1.0: USB hub found
[ 2262.290524] hub 5-4:1.0: 2 ports detected
[ 2263.076236] usb 5-4.1: new high speed USB device using ehci_hcd and address 3
[ 2263.208551] usb 5-4.1: configuration #1 chosen from 1 choice
[ 2263.428200] usb 5-4.2: new high speed USB device using ehci_hcd and address 4
[ 2263.568254] usb 5-4.2: configuration #1 chosen from 1 choice
[ 2263.573460] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7B04
[ 2263.575479] usbcore: registered new interface driver usblp
[ 2263.964411] usbcore: registered new interface driver libusual
[ 2264.055714] Initializing USB Mass Storage driver...
[ 2264.080617] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2264.090854] usbcore: registered new interface driver usb-storage
[ 2264.091382] USB Mass Storage support registered.
[ 2264.091957] usb-storage: device found at 4
[ 2264.091966] usb-storage: waiting for device to settle before scanning
[ 2269.089370] usb-storage: device scan complete
[ 2274.660194] usb 5-4.2: reset high speed USB device using ehci_hcd and address 4
[ 2289.732566] usb 5-4.2: device descriptor read/64, error -110
[ 2304.912270] usb 5-4.2: device descriptor read/64, error -110
[ 2305.088138] usb 5-4.2: reset high speed USB device using ehci_hcd and address 4
[ 2320.160240] usb 5-4.2: device descriptor read/64, error -110
[ 2335.336192] usb 5-4.2: device descriptor read/64, error -110
[ 2335.512198] usb 5-4.2: reset high speed USB device using ehci_hcd and address 4
[ 2345.920047] usb 5-4.2: device not accepting address 4, error -110
[ 2346.008147] usb 5-4.2: reset high speed USB device using ehci_hcd and address 4
[ 2356.420076] usb 5-4.2: device not accepting address 4, error -110
[ 2356.421894] scsi 2:0:0:0: Device offlined - not ready after error recovery
[ 2356.423712] usb 5-4.2: USB disconnect, address 4
[ 2356.516230] usb 5-4.2: new high speed USB device using ehci_hcd and address 5
[ 2371.588199] usb 5-4.2: device descriptor read/64, error -110
[ 2386.768183] usb 5-4.2: device descriptor read/64, error -110
[ 2386.944161] usb 5-4.2: new high speed USB device using ehci_hcd and address 6
[ 2402.016278] usb 5-4.2: device descriptor read/64, error -110
[ 2417.192253] usb 5-4.2: device descriptor read/64, error -110
[ 2417.386777] usb 5-4.2: new high speed USB device using ehci_hcd and address 7
[ 2427.792036] usb 5-4.2: device not accepting address 7, error -110
[ 2427.880198] usb 5-4.2: new high speed USB device using ehci_hcd and address 8
[ 2438.288031] usb 5-4.2: device not accepting address 8, error -110
[ 2438.289633] hub 5-4:1.0: unable to enumerate USB device on port 2

---


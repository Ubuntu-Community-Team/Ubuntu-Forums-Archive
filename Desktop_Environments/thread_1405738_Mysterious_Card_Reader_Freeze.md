---
title: "Mysterious Card Reader Freeze"
date: 2010-02-13
forum: Desktop Environments
---

### Post by frank.trampe on 2010-02-13
I am running 9.10 x86-64 with kernel 2.6.31-19-generic on an A.M.D. Phenom II X4 system with an ASUS M3A76-CM motherboard . All of the packages are current . Everything had worked quite well since I upgraded from 9.04 ( several months ago ) until I tried copying files from a Secure Digital card through a SanDisk MobileMate SD+ . Just a few seconds after I connected it , the display froze , the num lock and caps lock froze , and I could not switch to a text console . I have repeated this several times and have encountered the same result each time . Sometimes the logs show absolutely nothing , sometimes they show something like this {
```
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.540066] usb 2-2: new high speed USB device using ehci_hcd and address 3
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.706210] usb 2-2: configuration #1 chosen from 1 choice
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.916528] Initializing USB Mass Storage driver...
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.917256] scsi6 : SCSI emulation for USB Mass Storage devices
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.917658] usbcore: registered new interface driver usb-storage
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.917666] USB Mass Storage support registered.
```
} in messages and like this {
```
Feb 12 14:33:59 Sir-Norton-1 kernel: [947982.540066] usb 2-2: new high speed USB device using ehci_hcd and address 3
```
} in kern .

These problems do not occur in recovery mode . I have done a great deal of searching on this topic and have found nothing .

---


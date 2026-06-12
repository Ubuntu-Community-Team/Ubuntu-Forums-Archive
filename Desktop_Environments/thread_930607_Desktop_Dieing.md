---
title: "Desktop Dieing"
date: 2008-09-26
forum: Desktop Environments
---

### Post by rkathey on 2008-09-26
I'm running Ubuntu 7.10 on a home built machine.  Its run fine since the 7.10 initial release but recently its dieing with a signal 15.  It doesn't freeze up, it just shuts down.  At first I thought it was my hard disk since it seems to happen when I'm doing some heavy crunching.  I created a Ubuntu 8 Live CD and ran the memory test and it died again (no hard disk activity) so now I'm assuming bad memory but would like to know for sure.  Any suggestions?

Here's some log stuff.  Note, I get a lot of the USB messages in the log.

Sep 25 06:57:05 comp1 kernel: [33400.535008] mtrr: type mismatch for 3c000000,4000000 old: write-back new: write-combining
Sep 25 06:57:07 comp1 kernel: [33402.326307] usb 2-4: new full speed USB device using ohci_hcd and address 12
Sep 25 06:57:08 comp1 kernel: [33403.068790] usb 2-4: new full speed USB device using ohci_hcd and address 13
Sep 25 06:57:08 comp1 kernel: [33403.811281] usb 2-4: new full speed USB device using ohci_hcd and address 14
Sep 25 06:57:09 comp1 kernel: [33404.394090] usb 2-4: new full speed USB device using ohci_hcd and address 15
Sep 25 06:57:18 comp1 exiting on signal 15

Here's the mtrr output
output of cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd8000000 (3456MB), size=  64MB: write-combining, count=1
reg02: base=0x3bf00000 ( 959MB), size=   1MB: uncachable, count=1

---


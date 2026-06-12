---
title: "Eject volume error in Thunar (8.04 fluxbox)"
date: 2008-05-07
forum: Desktop Environments
---

### Post by leeyee on 2008-05-07
hi guys,

I have a removable hard disk with 3 partitions, i plugged it and can visit it easily in Thunar like we do in Nautilus. However, when i want to unmount it(Right Click on the volume -> Eject Volume), it pops up a window with "Wring data to device" and then gives error info: "Failed to eject volume, an unknown error occurred". Ironically, when i typed in "mount" in terminal, it showed me that removable HD had been unmounted.

More confusing thing is, when I use USB stick, it mounts and unmounts without this problem.

Here is the output of 
```
tail -f /var/log/messages
```
> May  8 08:21:43 alimus kernel: [ 4842.598310] usb 4-2: new high speed USB device using ehci_hcd and address 4
May  8 08:21:43 alimus kernel: [ 4842.732774] usb 4-2: configuration #1 chosen from 1 choice
May  8 08:21:43 alimus kernel: [ 4842.757440] scsi3 : SCSI emulation for USB Mass Storage devices
May  8 08:21:49 alimus kernel: [ 4848.347849] scsi 3:0:0:0: Direct-Access     SAMSUNG  HM080HC          AM10 PQ: 0 ANSI: 0
May  8 08:21:49 alimus kernel: [ 4848.362425] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  8 08:21:49 alimus kernel: [ 4848.363418] sd 3:0:0:0: [sdb] Write Protect is off
May  8 08:21:49 alimus kernel: [ 4848.364790] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  8 08:21:49 alimus kernel: [ 4848.365666] sd 3:0:0:0: [sdb] Write Protect is off
May  8 08:21:49 alimus kernel: [ 4848.365691]  sdb: sdb1 sdb2 < sdb5 sdb6 >
May  8 08:21:49 alimus kernel: [ 1710.921562] sd 3:0:0:0: [sdb] Attached SCSI disk
May  8 08:21:49 alimus kernel: [ 1710.921610] sd 3:0:0:0: Attached scsi generic sg2 type 0
May  8 08:21:55 alimus kernel: [ 2080.805258] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May  8 08:21:55 alimus kernel: [ 2080.806648] sd 3:0:0:0: [sdb] Write Protect is off
May  8 08:21:57 alimus kernel: [ 2080.806662]  sdb: sdb1 sdb2 < sdb5 sdb6 >


P.S. I also tried in Nautilus (Gnome), it works fine. So i guess it might be a problem of Thunar. Or because it's in fluxbox that something might not be triggered up which should be in Gnome environment.

---

### Post by MeanderingCode on 2008-08-06
Other info relevent is that i need to remove the ehci_hcd (USB 2) kernel module on my machine because i get constant address resets [when ehci_hcd is managing usb storage], so i'm running the external flash drive on uhci_hcd (USB 1.1) when this happens.

Anyone else?

---


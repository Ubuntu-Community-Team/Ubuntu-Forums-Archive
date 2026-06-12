---
title: "Please help get USB stick working."
date: 2009-05-01
forum: General Help
---

### Post by miatawnt2b on 2009-05-01
I am currently running Jaunty, and installed via upgrade.  I am having issues with a USB stick (which has never worked in ubuntu but works fine in windows) 

the following is in the syslog.
```

May  1 11:37:51 miata kernel: [ 3421.616081] usb 1-1: new high speed USB device using ehci_hcd and address 5
May  1 11:37:51 miata kernel: [ 3421.794732] usb 1-1: configuration #1 chosen from 1 choice
May  1 11:37:51 miata kernel: [ 3421.836670] scsi4 : SCSI emulation for USB Mass Storage devices
May  1 11:37:51 miata kernel: [ 3421.839365] usb-storage: device found at 5
May  1 11:37:51 miata kernel: [ 3421.839372] usb-storage: waiting for device to settle before scanning
May  1 11:37:56 miata kernel: [ 3426.836241] usb-storage: device scan complete
May  1 11:37:56 miata kernel: [ 3426.836867] scsi 4:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
May  1 11:37:56 miata kernel: [ 3426.842385] sd 4:0:0:0: [sdc] 2039808 512-byte hardware sectors: (1.04 GB/996 MiB)
May  1 11:37:56 miata kernel: [ 3426.880376] sd 4:0:0:0: [sdc] Write Protect is off
May  1 11:37:56 miata kernel: [ 3426.880380] sd 4:0:0:0: [sdc] Mode Sense: 0b 00 00 08
May  1 11:37:56 miata kernel: [ 3426.880382] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May  1 11:37:56 miata kernel: [ 3426.891021] sd 4:0:0:0: [sdc] 2039808 512-byte hardware sectors: (1.04 GB/996 MiB)
May  1 11:37:56 miata kernel: [ 3426.891645] sd 4:0:0:0: [sdc] Write Protect is off
May  1 11:37:56 miata kernel: [ 3426.891648] sd 4:0:0:0: [sdc] Mode Sense: 0b 00 00 08
May  1 11:37:56 miata kernel: [ 3426.891650] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May  1 11:37:56 miata kernel: [ 3426.891655]  sdc: sdc1
May  1 11:37:56 miata kernel: [ 3426.893119] sd 4:0:0:0: [sdc] Attached SCSI removable disk
May  1 11:37:56 miata kernel: [ 3426.893197] sd 4:0:0:0: Attached scsi generic sg3 type 0
May  1 11:38:26 miata kernel: [ 3457.112079] usb 1-1: reset high speed USB device using ehci_hcd and address 5
May  1 11:38:57 miata kernel: [ 3488.112083] usb 1-1: reset high speed USB device using ehci_hcd and address 5
May  1 11:39:28 miata kernel: [ 3519.116070] usb 1-1: reset high speed USB device using ehci_hcd and address 5

```

It appears that the kernel sees the stick and knows what it is, but I cannot mount it.

-J

---

### Post by garythegoth on 2009-05-01
What brand is the flash?

---

### Post by miatawnt2b on 2009-05-01
Not sure.  There is no brand on the case. It's a vendor freebie. Is there some way I can possible get more info through the kernel?
-J

---


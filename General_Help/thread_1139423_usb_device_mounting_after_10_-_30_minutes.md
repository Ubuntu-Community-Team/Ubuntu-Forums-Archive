---
title: "usb device mounting after 10 - 30 minutes"
date: 2009-04-27
forum: General Help
---

### Post by jithin1987 on 2009-04-27
I am using ubuntu jaunty.
My usb device is not mountig dmesg says
[ 2115.196304] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2115.385455] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2115.573328] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2115.761286] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2115.949417] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2116.137325] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2116.324420] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2116.513449] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2116.701306] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2116.889331] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2117.077282] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2117.268308] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2117.460279] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2117.648285] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2117.839795] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2118.032313] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2118.220411] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2118.408413] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2118.596415] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2118.784287] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2118.972443] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2119.164455] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2119.352456] hub 2-0:1.0: unable to enumerate USB device on port 6


I am now using 2.6.30.rc3 kernel. Problem exists with 2.6.28-11 kernel also. Please help me to resolve this issue.

---

### Post by jithin1987 on 2009-04-27
dmesg says this before it detected usb device.
[ 2381.384447] hub 2-0:1.0: unable to enumerate USB device on port 6
[ 2381.628089] usb 2-6: new high speed USB device using ehci_hcd and address 99
[ 2381.776192] usb 2-6: configuration #1 chosen from 1 choice
[ 2381.809828] Initializing USB Mass Storage driver...
[ 2381.857332] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2381.860103] usbcore: registered new interface driver usb-storage
[ 2381.860113] USB Mass Storage support registered.
[ 2381.861270] usb-storage: device found at 99
[ 2381.861277] usb-storage: waiting for device to settle before scanning
[ 2386.860395] usb-storage: device scan complete
[ 2386.861042] scsi 6:0:0:0: Direct-Access     TOSHIBA  MK3252GSX        LV01 PQ: 0 ANSI: 0
[ 2386.864381] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 2386.865224] sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[ 2386.865965] sd 6:0:0:0: [sdb] Write Protect is off
[ 2386.865974] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2386.865980] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2386.872686] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2386.872697]  sdb: sdb1
[ 2389.162270] sd 6:0:0:0: [sdb] Attached SCSI disk

---

### Post by blakkandekka on 2009-04-28
I'm having a similar problem.  IS it related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998") perhaps?

---

### Post by jithin1987 on 2009-04-28
I have filed a separate bug, but no ones looking into it so far,
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360400)

---


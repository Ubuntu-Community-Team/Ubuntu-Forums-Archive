---
title: "External USB drive disconnects at seemingly random times"
date: 2008-12-10
forum: General Help
---

### Post by ADINSX on 2008-12-10
I have a 750GB external HDD. It automounts just fine, and works as well as it should (I can read, write, and all that jazz). But it unmounts (or disconnects) randomly, and I cannot for the life of me figure out how to fix this. Sometimes when it disconnects, it immediately reconnects and remounts (well, tries to remount at least. I have to do a jfs_fsck first). Other times it simply "partially" reconnects, or something. It shows as being connected in my dmesg:

```
[ 4203.692201] usb 3-2: new high speed USB device using ehci_hcd and address 4
[ 4203.839486] usb 3-2: configuration #1 chosen from 1 choice
[ 4203.841380] scsi10 : SCSI emulation for USB Mass Storage devices
[ 4203.842525] usb-storage: device found at 4
[ 4203.842530] usb-storage: waiting for device to settle before scanning
[ 4208.840420] usb-storage: device scan complete
[ 4208.840975] scsi 10:0:0:0: Direct-Access     Maxtor   OneTouch         0121 PQ: 0 ANSI: 4
[ 4208.844942] sd 10:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
[ 4208.845693] sd 10:0:0:0: [sdc] Write Protect is off
[ 4208.845698] sd 10:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[ 4208.845702] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 4208.846438] sd 10:0:0:0: [sdc] 1465149168 512-byte hardware sectors (750156 MB)
[ 4208.847186] sd 10:0:0:0: [sdc] Write Protect is off
[ 4208.847191] sd 10:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[ 4208.847195] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 4208.847201]  sdc: sdc1 sdc3
[ 4217.725742] sd 10:0:0:0: [sdc] Attached SCSI disk
[ 4217.728296] sd 10:0:0:0: Attached scsi generic sg2 type 0

```

But when I do an ls -l /dev/disk/by-path, it only lists sdc, not sdc1 and sdc3.

When it does this "partial" reconnect, I can still read from it just fine, because I can do a cat /dev/sdc, and it reads and the hard drive does its thing just fine. So that leaves me wondering, why won't ubuntu recognize the individual partitions? Why does it randomly disconnect in the first place? Why does is it able to reconnect successfully sometimes, and not able to at other times?

This is incredibly frustrating. I have ruled out as being an HDD issue, as this happens with other external HDDs I have as well. It is also not a computer issue, as I can still *read* from the device just fine (at least the raw data).

I couldn't seem to find any answers to my question no matter how hard I looked, so I really hope someone can help me. :(

---

### Post by doctorbighands on 2008-12-10
Could it be a matter of you plugging into the USB ports on the front side of the machine (assuming you're using a desktop and not a laptop)? Those front ports are notorious for providing erratic voltages. If it drops below a certain voltage, even for a moment, it would cease to power your drive and it would, of course, unmount itself.

If you're using a desktop machine, try plugging into one of the USB ports in the rear, just as a troubleshooting step.

---

### Post by ADINSX on 2008-12-10
> **doctorbighands said:**
> Could it be a matter of you plugging into the USB ports on the front side of the machine (assuming you're using a desktop and not a laptop)? Those front ports are notorious for providing erratic voltages. If it drops below a certain voltage, even for a moment, it would cease to power your drive and it would, of course, unmount itself.

If you're using a desktop machine, try plugging into one of the USB ports in the rear, just as a troubleshooting step.

I am using a laptop, and I get the same result with all of my ports. Also I'm not sure if erratic voltage would explain why I sometimes cannot remount it afterwards.

---


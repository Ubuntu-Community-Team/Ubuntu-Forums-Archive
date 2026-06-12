---
title: "USB stick doesn't get mounted"
date: 2007-04-19
forum: Desktop Environments
---

### Post by Zaggy on 2007-04-19
dmesg output:
> [87246.437106] usb 5-1: USB disconnect, address 11
[87248.943599] usb 5-1: new high speed USB device using ehci_hcd and address 12
[87249.076446] usb 5-1: configuration #1 chosen from 1 choice
[87249.076688] scsi12 : SCSI emulation for USB Mass Storage devices
[87249.076784] usb-storage: device found at 12
[87249.076786] usb-storage: waiting for device to settle before scanning
[87254.072715] usb-storage: device scan complete
[87254.074713] scsi 12:0:0:0: Direct-Access     SanDisk  U3 Titanium      2.16 PQ: 0 ANSI: 2
[87254.080584] SCSI device sdc: 4013713 512-byte hdwr sectors (2055 MB)
[87254.083902] sdc: Write Protect is off
[87254.083906] sdc: Mode Sense: 03 00 00 00
[87254.083909] sdc: assuming drive cache: write through
[87254.093945] SCSI device sdc: 4013713 512-byte hdwr sectors (2055 MB)
[87254.097178] sdc: Write Protect is off
[87254.097181] sdc: Mode Sense: 03 00 00 00
[87254.097183] sdc: assuming drive cache: write through
[87254.097187]  sdc: sdc1
[87254.100874] sd 12:0:0:0: Attached scsi removable disk sdc
[87254.100910] sd 12:0:0:0: Attached scsi generic sg2 type 0

I removed the menu thingy that came with the stick with the manufacturer's removal tool, since it doesn't work on most pc's.
Stick used to work on dapper.

Manually mounting works just fine with:
cd /media
sudo mkdir stick
sudo mount /dev/sdc1 /media/stick -t vfat

I would prefer automount ofcourse ;-)

---

### Post by dcstar on 2007-04-22
> **Zaggy said:**
> 
.........
I would prefer automount ofcourse ;-)

You need to make sure the gnome-volume-manager process is running, check System-Preferences-Removable Drives and make sure the first two items are ticked.

---


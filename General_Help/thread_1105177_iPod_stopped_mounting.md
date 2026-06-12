---
title: "iPod stopped mounting"
date: 2009-03-24
forum: General Help
---

### Post by ryanferreri on 2009-03-24
Hello,

I am having some problems with my iPod Nano 3G on Ubuntu Intrepid. Yesterday I plugged it in and the icon came up showing it was mounted, but in Amarok it said that there was a lock file in the iPod filesystem somewhere and let me remove the lock. I was able to manage music on the device after that.

Now the iPod doesn't mount when I plug it in. I plugged it in and waited several minutes before I eventually had to unplug it. Here's the /var/log/messages output:

[25532.016019] usb 5-2: new high speed USB device using ehci_hcd and address 4
[25532.150183] usb 5-2: configuration #1 chosen from 2 choices
[25532.200064] scsi8 : SCSI emulation for USB Mass Storage devices
[25532.200385] usb-storage: device found at 4
[25532.200391] usb-storage: waiting for device to settle before scanning
[25537.200232] usb-storage: device scan complete
[25537.215474] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[25537.218386] sd 8:0:0:0: [sdg] 1941441 4096-byte hardware sectors (7952 MB)
[25537.219077] sd 8:0:0:0: [sdg] Write Protect is off
[25537.219082] sd 8:0:0:0: [sdg] Mode Sense: 68 00 00 08
[25537.219085] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[25537.220697] sd 8:0:0:0: [sdg] 1941441 4096-byte hardware sectors (7952 MB)
[25537.221316] sd 8:0:0:0: [sdg] Write Protect is off
[25537.221321] sd 8:0:0:0: [sdg] Mode Sense: 68 00 00 08
[25537.221324] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[25537.221328]  sdg: sdg1
[25537.222638] sd 8:0:0:0: [sdg] Attached SCSI removable disk
[25537.222774] sd 8:0:0:0: Attached scsi generic sg7 type 0
[25581.460292] usb 5-2: USB disconnect, address 4

---

### Post by Paul41 on 2009-03-24
Every once in a while my iPod won't mount. When that happens I reboot the iPod (hold down both the middle button and the menu button at the same time) and after the reboot it works.

---

### Post by Maheriano on 2009-03-24
Did you plug it into a Windows machine and not remove it safely?

---

### Post by ryanferreri on 2009-03-24
Nope. This iPod hasn't been plugged into a Windows machine since I originally set it up. I rebooted the thing. I'll see if it mounts when I get home.

---

### Post by ryanferreri on 2009-03-25
Thank you! Rebooting the iPod worked like a charm.

---


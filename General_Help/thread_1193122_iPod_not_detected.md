---
title: "iPod not detected"
date: 2009-06-21
forum: General Help
---

### Post by Crypen on 2009-06-21
Ubuntu isn't detecting my iPod Classic (5th generation). No icon appears in Computer and nothing new appears in /media. I've tested the cable and USB ports and they all turned out fine. The iPod's screen's displaying "Do not disconnect" and is not charging.

dmesg | tail returns

```
[ 4013.725585] sd 12:0:0:0: [sde] Mode Sense: 68 00 00 08
[ 4013.725590] sd 12:0:0:0: [sde] Assuming drive cache: write through
[ 4505.603568] usb 2-7: USB disconnect, address 10
[ 4510.236583] usb 2-7: new high speed USB device using ehci_hcd and address 11
[ 4510.371065] usb 2-7: configuration #1 chosen from 2 choices
[ 4510.371892] scsi13 : SCSI emulation for USB Mass Storage devices
[ 4510.376876] usb-storage: device found at 11
[ 4510.376881] usb-storage: waiting for device to settle before scanning
[ 4515.388099] usb-storage: device scan complete
[ 4515.388769] scsi 13:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

```Any help would be appreciated a lot. Thanks in advance.

---

### Post by hyperdude111 on 2009-06-21
I had a similar problem with an ipod mini. I had to wait a few hours then it would connect, and after doing that once it worked from then on.

---

### Post by Crypen on 2009-06-21
Left the iPod plugged in for 3 hours - got nothing. :(

Any more ideas?

---

### Post by Crypen on 2009-06-21
Problem fixed - turned out to just be a frozen screen. :o

---


---
title: "Edgy USB Device Mounting Hell"
date: 2007-03-06
forum: Desktop Environments
---

### Post by gilgongo on 2007-03-06
Aaaargh! WHAT IS IT WITH MOUNTING DRIVES???

Everything else in Edgy works perfectly except mounting stuff and accessing external hardware devices.

Can anyone tell me what the correct way of:

a) getting Ubuntu to recognise a USB Memorystick?

b) get it mounted so that I can write to it (and not have to access it as root)?

The device turns up on /var/log/messages as:

Mar  6 20:54:09 monoplane kernel: [17179765.612000] USB Mass Storage support registered.
Mar  6 20:54:14 monoplane kernel: [17179770.616000]   Vendor: Sony Eri  Model: Memory Stick      Rev: 0000
Mar  6 20:54:14 monoplane kernel: [17179770.616000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar  6 20:54:14 monoplane kernel: [17179770.616000] SCSI device sdb: 126912 512-byte hdwr sectors (65 MB)
Mar  6 20:54:14 monoplane kernel: [17179770.616000] sdb: Write Protect is off
Mar  6 20:54:14 monoplane kernel: [17179770.620000] SCSI device sdb: 126912 512-byte hdwr sectors (65 MB)
Mar  6 20:54:14 monoplane kernel: [17179770.620000] sdb: Write Protect is off
Mar  6 20:54:14 monoplane kernel: [17179770.620000]  sdb: sdb1
Mar  6 20:54:14 monoplane kernel: [17179770.636000] sd 2:0:0:0: Attached scsi removable disk sdb
Mar  6 20:54:14 monoplane kernel: [17179770.636000] sd 2:0:0:0: Attached scsi generic sg1 type 0

It used to work just fine with a nice little iPod icon on the desktop. Now today - nothing. 

Any ideas? And why this insane root mounting thing? I have to run Kino as root just to access my Firewire camera! What's that all about??

---

### Post by SilentSurfer on 2007-03-13
You should be able to mount it with ```
pmount sdb1
``` (as normal user).

Well, it should be mounted automatically...but that's my problem, too....

---


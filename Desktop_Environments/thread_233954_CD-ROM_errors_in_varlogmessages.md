---
title: "CD-ROM errors in /var/log/messages"
date: 2006-08-10
forum: Desktop Environments
---

### Post by ojai on 2006-08-10
Hi,

I just noticed that on all of my Dapper installs (which includes laptops and desktops) I see the following message in my /var/log/messages:

Aug 10 15:46:04 mybox kernel: hda: tray open
Aug 10 15:46:04 mybox kernel: end_request: I/O error, dev hda, sector 0
Aug 10 15:46:04 mybox kernel: hda: tray open
Aug 10 15:46:04 mybox kernel: end_request: I/O error, dev hda, sector 4

Does anyone know how to either disable whatever check is being done there or if it's possible to edit a config file to quit writing that info to the syslog?

I also see this occasionally but it's not as common as the above:

Aug  8 10:22:12 mybox kernel: end_request: I/O error, dev hdc, sector 4
Aug  8 10:22:12 mybox kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug  8 10:22:12 mybox kernel: hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Aug  8 10:22:12 mybox kernel: ide: failed opcode was: unknown

Whenever I see these messages, I immediately freak out thinking my HDD is about to breathe its last breath until I realize it's just the CD-ROM drive :-/

Thanks,

Carlos

---


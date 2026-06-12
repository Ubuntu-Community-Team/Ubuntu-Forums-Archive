---
title: "automount unreliable in icewm"
date: 2007-02-18
forum: Desktop Environments
---

### Post by mageus on 2007-02-18
I'm running IceWM and have gnome-volume-manager set to run in the startup file.  Automounting of CD-ROMs, CD-Rs, USB flash drives works fine.  However automounting of DVD's and DVD-recorded media is very unreliable.  Inserting DVD-type disc sometimes ends up having no action, and a perusal of /var/log/messages gives the following:


Feb 18 16:37:40 fishtank kernel: [17205427.328000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Feb 18 16:37:40 fishtank kernel: [17205427.328000] hdc: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Feb 18 16:37:40 fishtank kernel: [17205427.328000] ide: failed opcode was: unknown
Feb 18 16:37:40 fishtank kernel: [17205427.328000] end_request: I/O error, dev hdc, sector 64

Using mount, umount, and eject works perfectly fine for mounting these media that gnome-volume manager can't automount.


Is this a problem with gnome-volume-manager, or is it a problem with the file system?

---


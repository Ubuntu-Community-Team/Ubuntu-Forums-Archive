---
title: "Unable to mount CD-rom drive"
date: 2007-07-04
forum: Desktop Environments
---

### Post by Minilek on 2007-07-04
When I try to mount my cd-rom drive, I get the following error:

> minilek@minilek:~$ sudo mount /dev/hdc -t iso9660 -r /cdrom
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I look at dmesg, I see this:

> [429964.667669] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[429964.667676] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[429964.667679] ide: failed opcode was: unknown
[429964.667681] end_request: I/O error, dev hdc, sector 64
[429964.667973] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

I'm confident it's not a physical problem with the CD-rom drive, because I can listen to music CD's perfectly as follows:

> minilek@minilek:~$ sound-juicer -d /dev/hdc

Furthermore, I have two CD-rom drives in my desktop, and I get the same problem with both (not able to mount, but able to use sound-juicer).

Anyone know what might be going on, and how I can fix it?

---

### Post by garataidan on 2007-07-06
Hi,

I believe that you would install the packages pmount and hal for automount.

---


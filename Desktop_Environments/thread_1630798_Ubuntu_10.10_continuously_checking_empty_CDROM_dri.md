---
title: "Ubuntu 10.10 continuously checking empty CDROM drive"
date: 2010-11-25
forum: Desktop Environments
---

### Post by 77fx on 2010-11-25
I've just installed Ubuntu desktop 10.10 (32 bit). No matter what programs I run, the CD-ROM (DVD-ROM) drive is checking for a new CD/DVD every 5 seconds or so (even if no applications are running). It is quite annoying because of its robotic noise. The drive is empty. How could this be turned off? Is the media manager misconfigured by default?

---

### Post by 77fx on 2010-11-26
Meanwhile I looked at dmesg and discovered that there is an error with my CD-ROM.
I have 2 SATA disks, ata1 and ata2, and 2 SATA CDs, ata3 and ata4. The problem is with ata4:
[    1.231510] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
[    1.342459] ata4.00: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x6
[    1.342462] ata4: SError: { HostInt 10B8B }
[    1.342465] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[    1.342476] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[    1.342478]          res 51/24:03:00:00:00/00:00:00:00:00/a0 Emask 0x40 (internal error)
[    1.342481] ata4.00: status: { DRDY ERR }
[    1.342487] ata4: hard resetting link
[    1.816052] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.840162] ata4.00: configured for UDMA/100
[    1.951045] ata4: EH complete

I've tried to interpret the error message using [https://ata.wiki.kernel.org/index.php/Libata_error_messages](https://ata.wiki.kernel.org/index.php/Libata_error_messages)
So it was a:
Host bus adapter internal error 
10b to 8b decoding error occurred 
Maybe it's not Ubuntu's fault. I'll check how the CD-ROM is working in Windows...
My other CD-ROM drive (ata3) works fine.

---


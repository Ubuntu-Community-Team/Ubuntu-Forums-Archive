---
title: "ATA SATA Errors Dell D610 Ubuntu Dapper 6.06"
date: 2006-08-31
forum: Desktop Environments
---

### Post by thebasard on 2006-08-31
Folks,
I've been having intermittent issues where my system freezes temporarily (most of the time) and sometimes hard locks to the point where I have to hold down the power button and start all over.

**My system:**
Dell Latitude D610
60GB HD SATA
2GB RAM
[B]
Symptoms:[/B]
Mouse freezes
Keyboard input delayed
Whole system freezes

**What's in the logs?**
_from /var/log/messages:_
Aug 31 10:10:31 localhost kernel: [17183631.420000] ata2: PIO error
Aug 31 10:10:31 localhost kernel: [17183631.420000] ata2: no sense translation f or error 0x20

_from dmesg:_
[17183638.936000] ata2: PIO error
[17183638.936000] ata2: no sense translation for error 0x20
[17183638.936000] ata2: no sense translation for status: 0x51
[17183638.936000] ata2: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
[17183638.952000] ata2: BUG: timeout without command

Anyone have this same problem or know where I should start in diagnosing this?  I've run the onboard and 32bit diagnostics and no problems were found with the hard drive or controller.

Cheers,
CTD

---


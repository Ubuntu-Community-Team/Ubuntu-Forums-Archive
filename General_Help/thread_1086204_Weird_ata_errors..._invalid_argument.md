---
title: "Weird ata errors... invalid argument?"
date: 2009-03-03
forum: General Help
---

### Post by personwholives on 2009-03-03
I keep getting errors that say this:

```
[73809.259794] it821x: can't process command 0xEA
[73809.259813] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[73809.259818] ata2.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0 
[73809.259819]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x80 (invalid argument)
[73809.267988] it821x: can't process command 0x27
[73809.268004] ata2.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 0
[73809.268009] ata2.00: configured for PIO
[73809.268017] ata2: EH complete
```

Any idea why my computer seems to think there are a whole bunch of bad commands going to my ATA?  This doesn't seem to be a dead drive, as every other thread on the matter seems to say.  Is it picking the wrong hardware driver, maybe?  Or is something more dangerous going on?  The system works, I just get a bunch of these messages in my log.

Thanks in advance,
personwholives

---


---
title: "dvd slows during read"
date: 2009-01-21
forum: General Help
---

### Post by reader4 on 2009-01-21
I just setup a new system and ran into trouble today with my DVD RW while ripping CDs.  The first several songs (and CDs) ripped just fine, but after some time the speed slows to a crawl... I can hear the drive speed up, HDD write, then CD slow down for every read operation.  I can see these things:

```


$ dmesg |grep ata5
[    4.464232] ata5: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
[    4.808496] ata5.01: ATAPI: ATAPI   DVD A  DH20A4H, QP5A, max UDMA/66
[    4.840500] ata5.01: configured for UDMA/66
[49256.492030] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[49256.492037] ata5.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[49256.492040] ata5.01: status: { DRDY }
[49256.548016] ata5: soft resetting link
[49256.928501] ata5.01: configured for UDMA/66
[49256.928517] ata5: EH complete
[80904.860038] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[80904.860051] ata5.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[80904.860057] ata5.01: status: { DRDY }
[80904.916019] ata5: soft resetting link
[80905.296497] ata5.01: configured for UDMA/66
[80905.296513] ata5: EH complete

$ sudo hdparm -tT /dev/scd0

/dev/scd0:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error

```

But I'm not sure what else to check.  The problem seems to resolve on a reset but will come back.  Help?

---


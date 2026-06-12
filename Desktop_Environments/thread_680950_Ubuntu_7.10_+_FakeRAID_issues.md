---
title: "Ubuntu 7.10 + FakeRAID issues"
date: 2008-01-28
forum: Desktop Environments
---

### Post by andremedeiros on 2008-01-28
Hi guys.

I've been having a problem lately with my RAID partition, where I'm trying to view a movie and Totem suddenly crashes.

What I get in dmesg is a bit like:
```
Jan 28 18:31:52 zeus kernel: [  571.690798] ata7.00: exception Emask 0x10 SAct 0x6 SErr 0x780100 action 0x2
Jan 28 18:31:52 zeus kernel: [  571.690805] ata7.00: (irq_stat 0x08000000)
Jan 28 18:31:52 zeus kernel: [  571.690810] ata7.00: cmd 60/90:08:08:3f:eb/00:00:00:00:00/40 tag 1 cdb 0x0 data 73728 in
Jan 28 18:31:52 zeus kernel: [  571.690812]          res 40/00:14:98:3f:eb/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
Jan 28 18:31:52 zeus kernel: [  571.690817] ata7.00: cmd 60/20:10:98:3f:eb/00:00:00:00:00/40 tag 2 cdb 0x0 data 16384 in
Jan 28 18:31:52 zeus kernel: [  571.690819]          res 40/00:14:98:3f:eb/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
Jan 28 18:31:52 zeus kernel: [  572.001773] ata7: soft resetting port
Jan 28 18:31:52 zeus kernel: [  572.173504] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 28 18:31:52 zeus kernel: [  572.177422] ata7.00: configured for UDMA/133
Jan 28 18:31:52 zeus kernel: [  572.177433] ata7: EH complete
Jan 28 18:31:52 zeus kernel: [  572.177532] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Jan 28 18:31:52 zeus kernel: [  572.177546] sd 7:0:0:0: [sdc] Write Protect is off
Jan 28 18:31:52 zeus kernel: [  572.177550] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jan 28 18:31:52 zeus kernel: [  572.177708] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Any ideas?

---


---
title: "Error Messages About Hard Drive"
date: 2009-04-12
forum: General Help
---

### Post by Amphetaman on 2009-04-12
EDIT: After a bit of searching, I see this seems to be some sort of kernel bug. I apologize for the thread.

I am using the Ubuntu 8.10 LiveCD and I used the following command to wipe my hard drives (and check for errors):
```
sudo badblocks -b 4096 -c 128 -svw -t 0 /dev/sd*
```

It works just fine for sdb. However, when I run it on sda, it prints the following messages, but then continues: ```
[  265.990999] ata3: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[  265.991071] ata3: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[  265.991072]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
[  265.991238] ata3: ATA_REG 0x41 ERR_REG 0x0
[  265.991316] ata3: tag : dhfis dmafis sdbfis sacitve
[  265.991398] ata3: tag 0x0: 1 1 0 1  
[  265.991480] ata3.00: exception Emask 0x1 SAct 0x1 SErr 0x400000 action 0x6 frozen
[  265.991570] ata3.00: Ata error. fis:0x21
[  265.991647] ata3: SError: { Handshk }
[  265.991724] ata3.00: cmd 61/00:00:00:00:00/04:00:00:00:00/40 tag 0 ncq 524288 out
[  265.991725]          res 41/00:00:00:00:00/00:00:00:00:00/40 Emask 0x1 (device error)
[  265.991909] ata3.00: status: { DRDY ERR }
```

Additional inspection of dmesg yields this: ```
[  265.991986] ata3: hard resetting link
[  266.464045] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  266.574859] ata3.00: configured for UDMA/133
[  266.574868] ata3: EH complete
[  266.574968] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[  266.574991] sd 2:0:0:0: [sda] Write Protect is off
[  266.574993] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  266.575030] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Is this a problem with my hard drive? Maybe my controller? Is it something to worry about? Other hard drive diagnostic programs -- HDAT2 for instance -- don't seem to complain.

---


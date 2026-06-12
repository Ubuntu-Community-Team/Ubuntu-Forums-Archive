---
title: "1420n hard drive error"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by syssyphus on 2007-09-01
I am seeing the following error, does anyone know if it is really an error or not?

[  796.864000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  801.752000] ata1.00: exception Emask 0x2 SAct 0x1 SErr 0x0 action 0x2 frozen
[  801.752000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x1 FIS=005040a1:00000004)
[  801.752000] ata1.00: cmd 60/08:00:2e:5f:58/00:00:01:00:00/40 tag 0 cdb 0x0 data 4096 in
[  801.752000]          res 50/00:08:2e:5f:58/00:00:01:00:00/40 Emask 0x2 (HSM violation)
[  802.064000] ata1: soft resetting port
[  802.236000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  802.236000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[  802.236000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[  802.236000] ata1.00: configured for UDMA/133
[  802.236000] ata1: EH complete
[  802.236000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[  802.236000] sda: Write Protect is off
[  802.236000] sda: Mode Sense: 00 3a 00 00
[  802.236000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2473.168000] set_level status: 0
[ 2473.176000] set_level status: 0

---

### Post by flowbot on 2007-09-02
I get these same errors all the time with my Inspiron 1420 ... I've asked on IRC and somewhere else - the only answer I could get was that it's "probably" nothing to worry about. 

I came across some stuff on the kernel mailing list that suggests if a drive does this, it needs to be added to a blacklist for some function of the sata driver ... something like that.

Does anyone know anything more about this?

---


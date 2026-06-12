---
title: "Previously working SansDigital hardware RAID now an &quot;unknown partition table&quot;"
date: 2010-07-02
forum: Desktop Environments
---

### Post by sobeck on 2010-07-02
I have been happily using a hardware RAID from SansDigital which allowed me to boot into either Windows or Ubuntu, but about a week ago Ubuntu ceased to recognize the file system. The Disk Utility sees the entire 8TB as unallocated. Windows still sees all the data. This is true whether I connect using eSATA or USB.

I am running 10.04 LTS on a 64 bit AMD system. The system log indicates an "unknown partition table". I don't know what to do about that. Is it possible that some update installed an incompatible device driver?

From the System log:

ata1.00: ATA-7: H/W RAID5, 09
ata1.00: ATA-7: H/W RAID5, 0956, max UDMA/133
ata1.00: 15627714560 sectors, multi 16: LBA48 
ata1.00: configured for UDMA/133
ata1: EH complete
scsi 0:0:0:0: Direct-Access     ATA      H/W RAID5        0956 PQ: 0 ANSI: 5
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 0:0:0:0: [sda] 15627714560 512-byte logical blocks: (8.00 TB/7.27 TiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
sd 2:0:0:0: Attached scsi generic sg1 type 0
 sda:
sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
sd 2:0:0:0: [sdb] Write Protect is off
sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb:
scsi 3:0:0:0: CD-ROM            HL-DT-ST BD-RE  WH08LS20  1.00 PQ: 0 ANSI: 5
 unknown partition table


System log from two weeks ago when the file system was recognized.

ata1.00: ATA-7: H/W RAID5, 0956, max UDMA/133
ata1.00: 15627714560 sectors, multi 16: LBA48 
ata1.00: configured for UDMA/133
ata1: EH complete
scsi 0:0:0:0: Direct-Access     ATA      H/W RAID5        0956 PQ: 0 ANSI: 5
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 0:0:0:0: [sda] 15627714560 512-byte logical blocks: (8.00 TB/7.27 TiB)
scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
sd 2:0:0:0: Attached scsi generic sg1 type 0
sd 2:0:0:0: [sdb] Write Protect is off
sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---


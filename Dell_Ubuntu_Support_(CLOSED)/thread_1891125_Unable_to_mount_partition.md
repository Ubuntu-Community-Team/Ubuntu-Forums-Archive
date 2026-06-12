---
title: "Unable to mount partition"
date: 2011-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beparas on 2011-12-04
Hi all,
I am working on Ubuntu-10.4.
I have created 4 partition on my Dell Inspiron laptop.
Till yesterday its working fine. But today in the morning when I try to mount my one partition (named, Data), I am getting error attached here. 
 
The output of dmesg is given blow
> 
$ dmesg 

[  473.323263] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  473.323271] ata1.00: irq_stat 0x40000008
[  473.323278] ata1.00: failed command: READ FPDMA QUEUED
[  473.323291] ata1.00: cmd 60/08:00:56:1b:48/00:00:17:00:00/40 tag 0 ncq 4096 in
[  473.323294]          res 41/40:00:56:1b:48/00:00:17:00:00/40 Emask 0x409 (media error) <F>
[  473.323299] ata1.00: status: { DRDY ERR }
[  473.323304] ata1.00: error: { UNC }
[  473.323316] ata1: hard resetting link
[  473.640553] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  473.642880] ata1.00: configured for UDMA/133
[  473.642900] ata1: EH complete
[  476.229869] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  476.229875] ata1.00: irq_stat 0x40000008
[  476.229880] ata1.00: failed command: READ FPDMA QUEUED
[  476.229888] ata1.00: cmd 60/08:00:56:1b:48/00:00:17:00:00/40 tag 0 ncq 4096 in
[  476.229890]          res 41/40:00:56:1b:48/00:00:17:00:00/40 Emask 0x409 (media error) <F>
[  476.229894] ata1.00: status: { DRDY ERR }
[  476.229896] ata1.00: error: { UNC }
[  476.233384] ata1.00: configured for UDMA/133
[  476.233403] ata1: EH complete
[  478.803608] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  478.803614] ata1.00: irq_stat 0x40000008
[  478.803619] ata1.00: failed command: READ FPDMA QUEUED
[  478.803627] ata1.00: cmd 60/08:00:56:1b:48/00:00:17:00:00/40 tag 0 ncq 4096 in
[  478.803629]          res 41/40:00:56:1b:48/00:00:17:00:00/40 Emask 0x409 (media error) <F>
[  478.803632] ata1.00: status: { DRDY ERR }
[  478.803635] ata1.00: error: { UNC }
[  478.807165] ata1.00: configured for UDMA/133
[  478.807184] ata1: EH complete
[  481.377259] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  481.377265] ata1.00: irq_stat 0x40000008
[  481.377269] ata1.00: failed command: READ FPDMA QUEUED
[  481.377278] ata1.00: cmd 60/08:00:56:1b:48/00:00:17:00:00/40 tag 0 ncq 4096 in
[  481.377279]          res 41/40:00:56:1b:48/00:00:17:00:00/40 Emask 0x409 (media error) <F>
[  481.377283] ata1.00: status: { DRDY ERR }
[  481.377286] ata1.00: error: { UNC }
[  481.381409] ata1.00: configured for UDMA/133
[  481.381428] ata1: EH complete
[  483.950935] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  483.950941] ata1.00: irq_stat 0x40000008
[  483.950946] ata1.00: failed command: READ FPDMA QUEUED
[  483.950954] ata1.00: cmd 60/08:00:56:1b:48/00:00:17:00:00/40 tag 0 ncq 4096 in
[  483.950956]          res 41/40:00:56:1b:48/00:00:17:00:00/40 Emask 0x409 (media error) <F>
[  483.950960] ata1.00: status: { DRDY ERR }
[  483.950962] ata1.00: error: { UNC }
[  483.954915] ata1.00: configured for UDMA/133
[  483.954928] ata1: EH complete
[  486.524679] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  486.524687] ata1.00: irq_stat 0x40000008
[  486.524694] ata1.00: failed command: READ FPDMA QUEUED
[  486.524707] ata1.00: cmd 60/08:00:56:1b:48/00:00:17:00:00/40 tag 0 ncq 4096 in
[  486.524710]          res 41/40:00:56:1b:48/00:00:17:00:00/40 Emask 0x409 (media error) <F>
[  486.524716] ata1.00: status: { DRDY ERR }
[  486.524720] ata1.00: error: { UNC }
[  486.528425] ata1.00: configured for UDMA/133
[  486.528447] sd 0:0:0:0: [sda] Unhandled sense code
[  486.528451] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  486.528458] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  486.528466] Descriptor sense data with sense descriptors (in hex):
[  486.528470]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  486.528488]         17 48 1b 56 
[  486.528496] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  486.528506] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 17 48 1b 56 00 00 08 00
[  486.528523] end_request: I/O error, dev sda, sector 390601558
[  486.528547] JBD: IO error reading journal superblock
[  486.528556] EXT4-fs (sda6): 
[  486.528560] ata1: EH complete
[  486.528565] error loading journal
> 
$ uname -a
Linux paras-Inspiron-N5010 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux



---

### Post by jerrrys on 2011-12-06
I don't understand your error report, but

At times, when Nautilus fails; Disk Utility will work.

Is this just an ext4 partition used for date storage?  I have an HDD set up that way and if you store executable files on it you must put them in a folder or it can make it unmountable.

---


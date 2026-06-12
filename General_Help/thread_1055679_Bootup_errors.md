---
title: "Bootup errors"
date: 2009-01-30
forum: General Help
---

### Post by tuxxy on 2009-01-30
Im running a dualboot on one machine Intrepid/Jaunty and noticed the following errors at bootup of either OS, the machine will boot but takes some time and wanted to find the cause if possible.

Any ideas? 

```

[   11.744554] ata2.00: exception Emask 0x50 SAct 0x3 SErr 0x680900 action 0x6 frozen
[   11.744606] ata2.00: irq_stat 0x08000000, interface fatal error
[   11.744653] ata2: SError: { UnrecovData HostInt 10B8B BadCRC Handshk }
[   11.744703] ata2.00: cmd 60/f8:00:26:32:7c/00:00:01:00:00/40 tag 0 ncq 126976 in
[   11.744703]          res 40/00:0c:1e:33:7c/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
[   11.744798] ata2.00: status: { DRDY }
[   11.744844] ata2.00: cmd 60/08:08:1e:33:7c/00:00:01:00:00/40 tag 1 ncq 4096 in
[   11.744845]          res 40/00:0c:1e:33:7c/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
[   11.744940] ata2.00: status: { DRDY }
[   11.744987] ata2: hard resetting link
[   12.228020] ata2: softreset failed (device not ready)
[   12.228068] ata2: failed due to HW bug, retry pmp=0
[   12.392025] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   12.397378] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[   12.402761] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[   12.402763] ata2.00: configured for UDMA/133
[   12.402771] ata2: EH complete
[   12.402805] sd 1:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   12.402816] sd 1:0:0:0: [sda] Write Protect is off
[   12.402818] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.402837] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.535820] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x680900 action 0x6 frozen
[   12.535870] ata2.00: irq_stat 0x08000000, interface fatal error
[   12.535917] ata2: SError: { UnrecovData HostInt 10B8B BadCRC Handshk }
[   12.535967] ata2.00: cmd 60/20:00:8e:86:a5/00:00:00:00:00/40 tag 0 ncq 16384 in
[   12.535968]          res 40/00:04:8e:86:a5/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
[   12.536062] ata2.00: status: { DRDY }
[   12.536109] ata2: hard resetting link
[   13.016016] ata2: softreset failed (device not ready)
[   13.016071] ata2: failed due to HW bug, retry pmp=0
[   13.180026] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   13.185371] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[   13.190767] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[   13.190770] ata2.00: configured for UDMA/133
[   13.190775] ata2: EH complete
[   13.190802] sd 1:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   13.190813] sd 1:0:0:0: [sda] Write Protect is off
[   13.190815] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.190834] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.518080] ata2: limiting SATA link speed to 1.5 Gbps
[   13.518084] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x680900 action 0x6 frozen
[   13.518149] ata2.00: irq_stat 0x08000000, interface fatal error
[   13.518204] ata2: SError: { UnrecovData HostInt 10B8B BadCRC Handshk }
[   13.518261] ata2.00: cmd 60/20:00:5e:a8:7d/00:00:01:00:00/40 tag 0 ncq 16384 in
[   13.518262]          res 40/00:04:5e:a8:7d/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
[   13.518387] ata2.00: status: { DRDY }
[   13.518442] ata2: hard resetting link
[   14.000030] ata2: softreset failed (device not ready)
[   14.000085] ata2: failed due to HW bug, retry pmp=0
[   14.164025] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   14.169388] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[   14.174782] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[   14.174784] ata2.00: configured for UDMA/133
[   14.174789] ata2: EH complete

```

---

### Post by 73ckn797 on 2009-01-31
Do you think that the hard drive is failing? I have been working on a computer and it was extremely slow to boot. I removed the drive and replaced with another and problem was solved. Whenever I added back that drive the system experienced very slow boot up times.

---

### Post by tuxxy on 2009-01-31
> **73ckn797 said:**
> Do you think that the hard drive is failing? I have been working on a computer and it was extremely slow to boot. I removed the drive and replaced with another and problem was solved. Whenever I added back that drive the system experienced very slow boot up times.

Its a fairly new Samsung Spinpoint though, maybe Ill try another SATA cable.

---

### Post by lxowle on 2009-03-28
Did you ever manage to fix this? I get a very similar message under Jaunty beta:


 > 
 [    2.196065] ata2: failed due to HW bug, retry pmp=0
 [    2.360029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 [    2.360326] ata2.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66, ATAPI AN
 [    2.360342] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
 [    2.360788] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
 [    2.360790] ata2.00: configured for UDMA/66


I tried this link [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392/comments/11") with the all_generic_ide tag as a possible solution, but it doesn't appear to help.

Ubuntu does boot for me, and seems to work ok (I guess that is what is suggested by the messages above), but I did wonder why I get this error message now when I didn't under hardy.

---

### Post by Archmage on 2009-04-23
Is there a way to remove this error message?

---

### Post by dajasc on 2009-04-30
I get the same errors.  No actual problems with the drives.  It would be nice to know what the root cause of this is.

---

### Post by Ivan Kravchenko on 2009-05-07
I have the same errors too. 

   13.518080] ata2: limiting SATA link speed to 1.5 Gbps
[   13.518084] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x680900 action 0x6 frozen
[   13.518149] ata2.00: irq_stat 0x08000000, interface fatal error
[   13.518204] ata2: SError: { UnrecovData HostInt 10B8B BadCRC Handshk }
[   13.518261] ata2.00: cmd 60/20:00:5e:a8:7d/00:00:01:00:00/40 tag 0 ncq 16384 in
[   13.518262]          res 40/00:04:5e:a8:7d/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
[   13.518387] ata2.00: status: { DRDY }

---

### Post by exactt on 2009-05-28
this one might be related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392) .

please check if you got a ATI SB6xx/7xx SouthBridge and report there if you got the "Softreset failed (device not ready)" message in dmesg...

---

### Post by brian mcgee on 2009-10-06
I had similar errors. Replacing the SATA cable appears to have resolved the issue (at least, no more errors :P).

---


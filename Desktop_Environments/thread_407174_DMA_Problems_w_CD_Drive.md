---
title: "DMA Problems w/ CD Drive"
date: 2007-04-11
forum: Desktop Environments
---

### Post by djseto on 2007-04-11
I have just spent the last 4 hours trying to get DMA to work on CDROM/DVD Drive. I have just about gone crazy. I read the Ubuntu Guide: [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

but that didnt help. When I do a "sudo hdparm -i /dev/cdrom", I get:

-----------------------------------------------------------------------------
Model=DVDRW DRW-5S163, FwRev=YSG5, SerialNo=
Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
BuffType=unknown, BuffSize=0kB, MaxMultSect=0
(maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4
DMA modes: sdma0 sdma1 sdma2 sdma? mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2
AdvancedPM=no
Drive conforms to: Unspecified: ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

* signifies the current active mode
-----------------------------------------------------------------------------

as you can see, there is no asterisk to indicated the current active mode, however, when I type "sudo hdparm -d1 /dev/cdrom", I get:
-----------------------------------------------------------------------------
/dev/cdrom:
setting using_dma to 1 (on)
using_dma = 1 (on)
-----------------------------------------------------------------------------

I am running on 2.6.17-11. I have 1 IDE CD/DVD drive and 2 SATA drives. I have googled this to death. PLEASE PLEASE HELP.
Edit/Delete Message

---

### Post by djseto on 2007-04-12
bump

---

### Post by djseto on 2007-04-13
Anyone? I tried disabling IDE DMA in my Bios. No luck.

I am running on an Asus M2NPV-VM motherboard w/ two SATA drives and an IDE CD/DVD drive. This is a pretty common board, SOMEONE out there must be running a similar configuration.

---

### Post by djseto on 2007-04-13
bump again

---


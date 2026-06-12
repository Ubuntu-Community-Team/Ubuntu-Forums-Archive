---
title: "Ata issues on Suspend Resume Boot"
date: 2008-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LibertyShadow on 2008-07-22
First I was getting symptoms listed here:[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635")

But recently I would consider myself lucky to get those messages again :(

> 
Jul 22 08:48:14 Shadowcat-XPS kernel: [    0.589761] ata1.00: _GTF evaluation failed (AE 0x1001)
Jul 22 08:48:14 Shadowcat-XPS kernel: [    0.589832] ata2: port disabled. ignoring.
Jul 22 08:48:14 Shadowcat-XPS kernel: [    0.590301] ata3.00: _GTF evaluation failed (AE 0x1001)
Jul 22 08:48:14 Shadowcat-XPS kernel: [    1.182063] ata1.00: configured for UDMA/33
Jul 22 08:48:14 Shadowcat-XPS kernel: [    1.696860] ata3.00: configured for UDMA/133
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.356362] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.356970] ata3.00: BMDMA stat 0x5
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.357301] ata3.00: cmd 25/00:08:a6:f9:59/00:00:1c:00:00/e0 tag 0 dma 4096 in
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.357963] ata3.00: status: { DRDY ERR }
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.358333] ata3.00: error: { UNC }
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.363626] ata3.00: configured for UDMA/133
Jul 22 08:48:21 Shadowcat-XPS kernel: [    4.363660] ata3: EH complete
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.335480] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.336088] ata3.00: BMDMA stat 0x5
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.336442] ata3.00: cmd c8/00:38:72:ef:44/00:00:00:00:00/e6 tag 0 dma 28672 in
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.337140] ata3.00: status: { DRDY ERR }
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.337515] ata3.00: error: { UNC }
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.340246] ata3.00: configured for UDMA/133
Jul 22 08:48:28 Shadowcat-XPS kernel: [    5.340308] ata3: EH complete

> 
Jul 22 10:47:46 Shadowcat-XPS kernel: [   13.100206] ata3.00: ATA-8: SAMSUNG HM251JI, 2SS00_01, max UDMA7
Jul 22 10:47:46 Shadowcat-XPS kernel: [   13.100211] ata3.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 0/32)
Jul 22 10:47:46 Shadowcat-XPS kernel: [   13.101330] ata3.00: configured for UDMA/133
Jul 22 10:47:46 Shadowcat-XPS kernel: [   14.247743] EXT3-fs: mounted filesystem with ordered data mode.
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.669141] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.669154] ata3.00: BMDMA stat 0x25
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.669165] ata3.00: cmd c8/00:08:ea:9f:42/00:00:00:00:00/e8 tag 0 dma 4096 in
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.669173] ata3.00: status: { DRDY ERR }
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.669177] ata3.00: error: { UNC }
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.683163] ata3.00: configured for UDMA/133
Jul 22 10:48:47 Shadowcat-XPS kernel: [   61.683197] ata3: EH complete


I can no longer suspend / resume without getting these errors.  According to [http://ata.wiki.kernel.org/index.php/Libata_error_messages#ATA_error_expansion]("http://ata.wiki.kernel.org/index.php/Libata_error_messages#ATA_error_expansion")  my issue could be bad sectors on the disk.  I suppose I should be asking Dell how I have bad sectors after owning this xps m1330 for 2 months?  

I had to change the mode in the bios to ata when I installed Windows XP (arg...) and inherently, the flash cache module.  I was having problems ("frozen, {DRDY}") before this change as well as after.  I have tried setting "pci=nomsi" and "irqpool" and "all_generic_ide" in my boot options but nothing seems to be helping.  I just ran an fsck -f from runlevel 1 on my root filesystem but no problems were detected.   I am symbolically linking a few folders to an xfs file system (Music, Documents, .wine,.mozilla-thunderbird), but I don't think that this is related.

I am planning to install Ubuntu to another part of the disk later tonight.  I might try another distro (Open SuSE) just to see if this is a Ubuntu, kernel, or hardware issue.  

Any insight would be much appreciated!

---

### Post by LibertyShadow on 2008-07-22
I also have an inconsistency between the sizes of my partitions according to gparted and nautilus.  Is that normal behavior?  It has been going on since Day 1.

---

### Post by LibertyShadow on 2008-07-22
A failed suspend:

Anyone?

---

### Post by LibertyShadow on 2008-07-24
I installed hardy to another part of the drive, and have had no (related) problems yet.

---

### Post by atlas95 on 2008-07-24
I have this problem on my m1330 sometimes when I resume it; but after few second this disappear and I can use it.

---

### Post by LibertyShadow on 2008-07-29
> 
Jul 29 00:24:47 Shadowcat-XPS kernel: [   10.083284] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul 29 00:24:47 Shadowcat-XPS kernel: [   10.083302] ata3.00: cmd ca/00:30:e1:94:df/00:00:00:00:00/e4 tag 0 dma 24576 out
Jul 29 00:24:47 Shadowcat-XPS kernel: [   10.083305]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Jul 29 00:24:47 Shadowcat-XPS kernel: [   10.083311] ata3.00: status: { DRDY }
Jul 29 00:24:47 Shadowcat-XPS kernel: [   10.851719] ata3: port is slow to respond, please be patient (Status 0xd0)
Jul 29 00:24:47 Shadowcat-XPS kernel: [   12.095136] ata3: device not ready (errno=-16), forcing hardreset
Jul 29 00:24:47 Shadowcat-XPS kernel: [   12.095150] ata3: soft resetting link
Jul 29 00:24:47 Shadowcat-XPS kernel: [   12.242070] ata3.00: configured for UDMA/133
Jul 29 00:24:47 Shadowcat-XPS kernel: [   12.242097] ata3: EH complete


A hung up resume....and I really didn't tweak this install.  I guess I should go bug hunting.

EDIT:  I did add the fixes for the high frequency of parking yesterday...

---

### Post by LibertyShadow on 2008-08-23
I disabled smartctl (used for disk monitoring) by uninstalling smartmontools.  I have not had any issues in 3 weeks.

---


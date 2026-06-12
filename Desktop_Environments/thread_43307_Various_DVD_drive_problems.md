---
title: "Various DVD drive problems"
date: 2005-06-21
forum: Desktop Environments
---

### Post by unzari on 2005-06-21
I just moved from Fedora Core 3 to Ubuntu.  Now I'm having lots of problem with an old DVD drive that worked fine under Fedora.  It's not a disc problem, as I've tried many.

1)  Using "dd if=/dev/dvd of=dvd.iso" to rip the contents to a file system no longer works.  It fails with an I/O error as shown below.  The resulting file is only a few MB.

[INDENT]root@sal:/video # dd if=/dev/hdd of=dvd.iso
dd: reading `/dev/hdd': Input/output error
226600+0 records in
226600+0 records out
116019200 bytes transferred in 5.357110 seconds (21657050 bytes/sec)[/INDENT]

2) None of the video players (Totem, VLC, mplayer) I have can read the discs.

**From Totem:**
[INDENT]libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Invalid title IFO (VTS_02_0.IFO).
[00000239] dvdread demuxer error: fatal error in vts ifo
[00000239] dvdread demuxer error: read failed for block 0
[/INDENT]

This drive is too old for DMA, but again, it worked fine under Fedora.  Here is what 'hdparm' says about it.

[INDENT]root@sal:/video # hdparm -i /dev/dvd

/dev/dvd:

 Model=CREATIVEDVD-ROM DVD2240E 10/13/97, FwRev=1.5A, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:150}
 PIO modes:  pio0 pio1 pio2 pio4
 DMA modes:  sdma0 sdma1 sdma2 sdma? mdma0 mdma1 mdma2
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-4 X3T13 1153D revision 7:  2

 * signifies the current active mode[/INDENT]


  Anybody have any ideas?

---


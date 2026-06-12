---
title: "Movie file not working at correct speed"
date: 2005-12-21
forum: Desktop Environments
---

### Post by SniperX725 on 2005-12-21
When I try to play movies with totem-xine such as .avi they play fine with sound and everything but play about twice the speed they should which looks wierd.  I cant seem to find a post or fix for this problem.  I have run automatix and tried to install the codecs manually as well, and they are installed.  The wierd thing is MPlayer runs them fine, but for some movies it will play extremely choppy.  Also the speed is messed up with vlc.

gateway laptop
I am running ubuntu 5.10 32-bit
amd 64bit 3700+
1gig ram

Any help would be awsome.
P.S. Ubuntu is in my opinnion the best distro out there.

---

### Post by dlpfmVfH on 2005-12-21
did you enable dma for your harddisk...check this in a terminal with:

sudo hdparm -i /dev/*your harddisk number* (default is hda)

if the * in the udma modes it is enabled.

---

### Post by SniperX725 on 2005-12-22
I think so here is what happend after I did that.

andy@andylinux:~$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=FUJITSU MHU2100AT, FwRev=00000008, SerialNo=NQ04T5428KMH
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:

 * signifies the current active mode

---


---
title: "ubuntu running very slow"
date: 2006-06-24
forum: Desktop Environments
---

### Post by katesfb on 2006-06-24
Hi, recently installed ubuntu 6.06 and the installation went fine. However i have found that the system is running very slow - even applications such as terminal take a few seconds to load and normally quick applications such as firefox take an age to load. The computer is a P4 celeron 1700 with 256 meg of ram. I installed over the top of a previous mandrake 10 install but the root partition and swap space were both reformatted by the install - swap space is 500MB and root partition is 8.5 GB. The original mandrake system also had a boot partition of 47MB, this still exists and was not reformatted by the install (could this be causing the problems?). Essentially the system seems to run OK, just very slow. Any help you can give would be much apreciated.

Cheers.

---

### Post by alaaji on 2006-06-25
Hi katesfb.  Click on the link in my sig and find the link called "Pick the kernel that's right for your processor."  Hope it helps!

---

### Post by Abild on 2006-06-25
In my expirience 256mb ram simply isn't enough to run gnome with acceptable performance. You might want to check out xubuntu which comes with the xfce desktop enviroment. It's much lighter than gnome and should perform better on your machine.

Otherwise, you could simply upgrade your computer to at least 512mb ram. Ram is really cheap these days :)

---

### Post by 3rdalbum on 2006-06-25
I think the latest kernel is causing a slowdown. Dapper with the latest kernel = slow. Dapper with old Breezy kernel = fast (but silent). At least on my computer, anyway.

256Mb is definately enough to run standard Ubuntu at a good pace.

---

### Post by katesfb on 2006-07-01
Hi Guys - thanks for that. I tried setting the HD paramenters using HDparm and only got a minor increase in speed to a max of about 34 MB/sec which still seems pretty slow to me. See below.

/dev/hda:
 Timing cached reads:   1112 MB in  2.00 seconds = 556.08 MB/sec
 Timing buffered disk reads:  104 MB in  3.03 seconds =  34.33 MB/sec

Current settings are;

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38792/16/63, sectors = 39102336, start = 0

turning on unmaskirq has no effect. The hard drive is only about 3-4 years old so i should be able to get better than 34MB/sec out of it Or is that the best i can expect? The drive is a seagate barracuda ata100. A trace from the -i switch is below;

Model=ST320014A, FwRev=3.07, SerialNo=5JZCJNHE
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=39102336
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

Any ideas, any help you can give is much apreciated.

Cheers.

---


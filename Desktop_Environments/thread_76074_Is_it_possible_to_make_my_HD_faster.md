---
title: "Is it possible to make my HD faster ?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-14
I was reading some tutorials for linux and a I found one very interesting about hdparm.

This is the speedy I cant get in my machine:

[b]sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1228 MB in  2.00 seconds = 613.79 MB/sec
 Timing buffered disk reads:  124 MB in  3.01 seconds =  41.26 MB/sec[/b]


This is the data about my hard disk:

[b]sudo hdparm -i /dev/hda


/dev/hda:

 Model=SAMSUNG SP0802N, FwRev=TK200-04, SerialNo=0820J1FY443078
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156368016
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode[/b]


This tutorial suggests me to do:

[b]hdparm -m 16 /dev/hda
hdparm -a 16 /dev/hda
hdparm -u 1 /dev/hda[/b]

Is it dangerous ? Can I have lost of data or hardware failure with those commands ? Is it worth to enable it ? Do they really speed up the hard disk ?

Thanks.

TUTORIAL: [http://www.openslack.org/~piterpk/english/hdparm_en.html](http://www.openslack.org/~piterpk/english/hdparm_en.html)

---

### Post by Lord Illidan on 2005-10-14
What this tutorial is stating is how to enable dma...and it is already enabled on your machine..
Doing those commands will not harm your system. Use them, if you feel that it is unstable, just reboot. The changes are not permanent, unless you put them in a config file..

---

### Post by kurtkraut on 2005-10-14
[QUOTE=Lord Illidan]What this tutorial is stating is how to enable dma...and it is already enabled on your machine..
Doing those commands will not harm your system. Use them, if you feel that it is unstable, just reboot. The changes are not permanent, unless you put them in a config file..[/QUOTE]

But do they really speed up the hard disk ? Are the settings in the suggested commands right for better configuration ?

---


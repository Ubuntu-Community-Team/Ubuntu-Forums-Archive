---
title: "dual channel failure &amp; single channel errors"
date: 2011-06-25
forum: Desktop Environments
---

### Post by Ed W. on 2011-06-25
PC seems to run fine in single channel mode but monitor reports no input in dual channel mode and memtest86+ lists from 1-3 errors per pass in single channel mode.  Motherboard (Gigabyte P43T-ES3G) can't be set for the 1.65 volts required by the RAM (2x2 of OCZ3P1333LV4GK PC3 10666).  The mobo voltage choices are 1.6 or 1.7 volts.  I have tried both and increased the MCH voltage from 1.1 v to 1.2 v, but so far can't get it to run in dual channel mode at all and single channel mode seems to run fine but I still get errors in memtest86+.  Also tried optimized Bios settings and loosened memory timings (from 7-7-7-16 to 8-8-8-27 and tRFC 60 to 70) and reset Command Rate from 0 to 2.

CPU is Core 2 Quad @ 2.4 Ghz, PSU is rated at 400 watts, Video card is Gigabyte GT220.  Any help would be greatly appreciated.

---

### Post by tgalati4 on 2011-06-25
Try different RAM.  If you get errors with two other brands of RAM, then you have a defective motherboard.

---

### Post by Ed W. on 2011-06-26
Thanks tgalati4, for the help.  I will probably have to buy some more memory to do that.  So it will be a week or so before I can report the results.  What are the odds on both sticks of memory being bad?

Also I noticed that when one stick of memory is in either slot 1 or 2 that memtest86+ sees it correctly as DDR3, but when it is in either slot 3 or 4, memtest86+ sees it as DDR2.

---


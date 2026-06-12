---
title: "Slow disk transfer"
date: 2009-01-27
forum: General Help
---

### Post by KosteK94 on 2009-01-27
Hello, i've installed, formatted(ext3) and mounted my 160GB ATA disk, and that's my transfer:
```

/dev/sdb1:
Timing cached reads: 428 MB in 2.00 seconds = 214.36 MB/sec
Timing buffered disk reads: 6 MB in 3.45 seconds = 1.74 MB/sec

```
and that's hdparm -i /dev/sdb
```
 Model=Maxtor 6Y160P0                          , FwRev=YAR41BW0, SerialNo=Y44KPWAE            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=7936kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=320173056
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```
Anybode knows why it's only 2mb/s?
Transfer from that 160GB disk to disk with Ubuntu installed is good, but from Ubuntu disk to 160GB disk, it's slooooooow...
On google i've found many sites with that, but no info how to solve it.

---

### Post by jondecker76 on 2009-02-17
hdparm also only reports 1-2 MB/sec on my sata drive. Maked  ubuntu too slow to use on this system

---

### Post by handy on 2009-02-18
I just checked my iMac running Arch & I got 72.53 Mb/sec.

For all it's worth.

---

### Post by dcstar on 2009-02-18
> **handy said:**
> I just checked my iMac running Arch & I got 72.53 Mb/sec.

For all it's worth.

Mine:
```
root@dc-master:/home/dc# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1666 MB in  2.00 seconds = 832.93 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.41 MB/sec

root@dc-master:/home/dc# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1638 MB in  2.00 seconds = 818.81 MB/sec
 Timing buffered disk reads:  184 MB in  3.02 sec =  60.88 MB/sec

```

I believe that these are also only valid for PATA drives, I'm not sure if SATA drives report accurately.

---

### Post by handy on 2009-02-18
I just did it again with the following results:

handy ~  $  sudo hdparm -tT /dev/sda3
Password: 

/dev/sda3:
 Timing cached reads:   6436 MB in  2.00 seconds = 3225.14 MB/sec
 Timing buffered disk reads:  218 MB in  3.01 seconds =  72.44 MB/sec

Accurate?? :?:  :D

---

### Post by InFeh on 2009-02-18
Is this HDD external? I had an issue with large external SATA drives transferring fast on USB1.1, and 1.7 Mbps sounds about right. Now on 2.0, it's ALOT faster.

---


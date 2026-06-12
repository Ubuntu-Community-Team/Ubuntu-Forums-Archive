---
title: "ata/0 using lots of cpu in 8.10 xubuntu"
date: 2009-03-02
forum: Desktop Environments
---

### Post by lowbot on 2009-03-02
Is this normal? Top tells me that ata/0 keeps using a lot of cpu. Im not sure what it is. Is it my pata interface? Is it normal for it to be CPU hungry? Thanks.

---

### Post by wirespot on 2009-04-05
Bump. I'm also seeing this in Ubuntu when I'm doing something HDD-intensive, like mkfs, or even just hdparm -t. The hdparm benchmark drops to 1-3 MB/sec, whereas at the start of the system it was 40 MB/sec. And the thing that triggered this seems to be that mkfs. May have something to do with the fact I have 2 hdd, both on the same controller?*(sda and sdb).

---

### Post by wirespot on 2009-04-05
LE:*Moving one HDD on a different controller seems to have fixed the problem for me.

---

### Post by cyanics on 2009-05-23
Bump

I found this problem today after a fresh install of server 9.04 x86.

ATA/0 is at 40%-100% and grinds all IO on the system to a halt. hdparm -tT /dev/sde shows around 40MB/s when there is zero IO. But disk to disk transfers are in the range of 500Kb/s when using this one disk.

hdparm -i /dev/sde
```

/dev/sde:

 Model=Maxtor 6B250R0                          , FwRev=BAH41G10, SerialNo=B504FBLH
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=490234752
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```


hdparm -tT /dev/sde (with IO)
```

/dev/sde:
 Timing cached reads:     2 MB in  3.03 seconds = 676.41 kB/sec
 Timing buffered disk reads:    2 MB in  3.14 seconds = 652.19 kB/sec
```


hdparm -tT /dev/sde (without IO)
```
/dev/sde:
 Timing cached reads:   1050 MB in  2.00 seconds = 525.13 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.52 MB/sec
```


anyone got a lead? or any ideas?

---

### Post by GVaquerizo on 2009-06-08
I've just SOLVED it.
I had the same problem (laptop and Jaunty).
In dmesg appeared "clocksource tsc unstable"
After googling I found:
[http://kerneltrap.org/node/8306](http://kerneltrap.org/node/8306)
[http://electrobuntu.blogspot.com/2009/06/ubuntu-jaunty-congelado-explicacion-y.html](http://electrobuntu.blogspot.com/2009/06/ubuntu-jaunty-congelado-explicacion-y.html)

I tried starting kernel with one of this 3 options:
/vmlinuz-2.6.28-11-generic root=UUID=4d66890f-e2a1-4ef3-87f7-36e66132a5ec ro xforcevesa ***_clocksource=jiffies_***
/vmlinuz-2.6.28-11-generic root=UUID=4d66890f-e2a1-4ef3-87f7-36e66132a5ec ro xforcevesa ***_clocksource=acpi_pm_***
/vmlinuz-2.6.28-11-generic root=UUID=4d66890f-e2a1-4ef3-87f7-36e66132a5ec ro xforcevesa ***_clocksource=hpet_***

And only the first one (***_jiffies_***) worked! No more delays with ata/0
(I must say that my friend Malone showed me the way, as there seemed to be no relation between hard disk and TSC counter...)

---


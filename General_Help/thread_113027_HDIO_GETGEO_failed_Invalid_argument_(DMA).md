---
title: "HDIO_GETGEO failed: Invalid argument (DMA)"
date: 2006-01-05
forum: General Help
---

### Post by fig_jam_uk on 2006-01-05
Hey all i relly have become stuck on somthing!!! Im trying to enable DMA on both my CD/RW drive and DVD/RW drive but im coming to a dead end with all ive tried..

I have tried quite a few things and just keep getting the same problem...

[HTML]/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument[/HTML]

And when trying to enable DMA i get

[HTML]mark@Damn:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
mark@Damn:~$ sudo hdparm -d1 /dev/hdd[/HTML]

Ive tried adding 

[HTML]/dev/hdc {
dma = on
}

/dev/hdd {
dma = on
}[/HTML]

to the end of the hdparm.conf file and rebooting but still get the problem.

Im running Kernel -- 2.6.10-6-686
                             -- 1Gb Dual channel DDR
                             -- Nforce 4 ultra MOBO
                             -- both drives are samsung

If anybody has any pointers i`d be greatly appreciative :p

---

### Post by chovy on 2006-09-06
*bump* i'm getting the same problem.

---

### Post by Roger Gundberg on 2007-05-11
I dont,t quite have that issue but...
/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device (< what the heck is this?)
root@roger-desktop:/home/roger#

---

### Post by Myrgen on 2007-05-17
> **Roger Gundberg said:**
> I dont,t quite have that issue but...
/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device (< what the heck is this?)
root@roger-desktop:/home/roger#

I have the exact same issue.. Anyone has an idea? :)

---

### Post by derekguy on 2007-05-19
I have the same issue; am using Fiesty 7.04 (upgraded from Edgy) and I am trying to enable DMA.

```
sudo hdparm -d1 /dev/scd0
```

I was able to do this under Edgy and was loving the speed Grip ripped CDs and K9Copy/K3b did DVDs but now I am unable to burn DVD .iso's anymore. Ripping DVDs seems OK but CDs take a long time.

I get this error:

```
$ sudo hdparm -d 1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

I have no idea why i am unable to set this option anymore. This only seems to be a problem when I am burning DVD+R media. DVD-R's burn fine for some reason. This has been tested on many different discs. Any ideas why?

I am running a Compaq Presario B1800 notebook. The DVD multi drive in question is a Mashita DVD-RAM UJ-840S.

Cheers for any tips or hints.

---

### Post by grndslm on 2007-06-02
I'm getting the same error as derekguy above.

And when I do "sudo hdparm -iTt /dev/sda /dev/scd0" (both of these are ATA, btw...it's an old Dell Optiplex GX150), I get this:

```

/dev/sda:

 Model=ST340014A                               , FwRev=8.16    , SerialNo=5JXGC6W7            
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?8?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78125000
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

** Timing cached reads:   146 MB in  2.00 seconds =  72.88 MB/sec**
 Timing buffered disk reads:   72 MB in  3.11 seconds =  23.18 MB/sec

/dev/scd0:

 Model=TOSHIBA DVD-ROM SD-R5112                , FwRev=1031    , SerialNo=Z3RA201037          
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

 [B]Timing cached reads:   124 MB in  2.57 seconds =  48.29 MB/sec
 Timing buffered disk reads:   10 MB in  3.67 seconds =   2.73 MB/sec[/B]
```
First, those transfer speeds can't be that good for a 7200rpm seagate...

Second, why do these ATA drives come up as /dev/sd & /dev/scd0?

And finally, is hdparm *meant* to be used on both drives?  I thought it was just one or the other...

---

### Post by grndslm on 2007-06-08
bump diddilyump!

---

### Post by cor2y on 2007-06-13
i can't say i have any issues burning but what was a simple 15 min or less time to create 500mb   cd-r  iso and burn at full rated 20x now somehow takes about 45 mins for each process, 45min  to create the iso and another 45 mins to burn.
I can say that i never had these slow speeds in  Edgy, Dapper or Hoary.
At first i thought it was gnome baker so i switched to k3b but the speeds were still the same.
Then i check DMS (which i believe is enabled by default) and that error about
HDIO_GETGEO failed is showing up although dma is listed as being enable on both burners.

So any idea what is the cause or how to fix the error.

---

### Post by julipanno on 2007-06-13
> **fig_jam_uk said:**
> Hey all i relly have become stuck on somthing!!! Im trying to enable DMA on both my CD/RW drive and DVD/RW drive but im coming to a dead end with all ive tried..

I am having the same problem myself and found this page which seems to provide an explanation and a solution:
[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive)

---


---
title: "hdparm -v &amp; -t issues"
date: 2005-12-12
forum: General Help
---

### Post by ShirishAg75 on 2005-12-12
Hi all,
       Recently while reading a tech magazine, I came across this article which told me that one could change the hard disk parameters & improve the booting up as well as general work in Ubuntu 5.10 . Noob here, This is my output from running hdparm -v /dev/hda. The chipset I have is i845 GLM & the drive is Samsung 80 GB PATA 133. It was also written in the article as well as the man page that manipulating drive settings can cause problems if the chipset is not supported or the drive doesn't support the setting fully.

Now my questions are :- 
1. Now how to know whether the chipset is being supported or not as well what drive settings are fully supported. 

when giving ```
hdparm -t /dev/hda
``` it gives 
          /dev/hda :
   Timing buffered disk reads: 12 MB in 3.21 seconds=3.74 MB/sec

Now I know this can be increased quite dramatically without endangering the hdd but not sure how to go about configuring things, can anyone help. Below is the hdparm -v settings as of right now, the only change I made was the -d1 flag till now.

```
shirishag75@ubuntu:~$ hdparm -v /dev/hda
/dev/hda: Permission denied
shirishag75@ubuntu:~$ sudo hdparm -v /dev/hda
Password:
```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156368016, start = 0
 
 ```
sudo hdparm -Tt /dev/hda
```

/dev/hda:
 Timing cached reads:   1088 MB in  2.00 seconds = 543.81 MB/sec
 Timing buffered disk reads:   24 MB in  3.05 seconds =   7.87 MB/sec

```
shirishag75@ubuntu:~$ sudo hdparm -i /dev/hda
```

/dev/hda:

 Model=SAMSUNG SP0802N, FwRev=TK100-24, SerialNo=S00JJ10X390473
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=156368016
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode
 
```
sudo hdparm -I /dev/hda
```

/dev/hda:

ATA device, with non-removable media
        Model Number:       SAMSUNG SP0802N
        Serial Number:      S00JJ10X390473
        Firmware Revision:  TK100-24
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   64761
        heads           16      1
        sectors/track   63      255
        --
        CHS current addressable sectors:   16514055
        LBA    user addressable sectors:  156368016
        LBA48  user addressable sectors:  156368016
        device size with M = 1024*1024:       76351 MBytes
        device size with M = 1000*1000:       80060 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 1
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    FLUSH CACHE EXT command
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    48-bit Address feature set
                Automatic Acoustic Management feature set
                SET MAX security extension
           *    DOWNLOAD MICROCODE cmd
           *    SMART self-test
           *    SMART error logging
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        28min for SECURITY ERASE UNIT. 28min for ENHANCED SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

I gave sudo hdparm -d1 -X69 -c1 -M192 -A1 -a64 -m 16 /dev/hda
now is there something better than this can be achieved. Also -p (PIO) option is supposed to be unstable. Can something be known about that? The manual was written this april so seems to be a recent addition.

---

### Post by ShirishAg75 on 2005-12-13
what no replies?

---


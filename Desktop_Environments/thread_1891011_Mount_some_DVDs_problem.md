---
title: "Mount some DVDs problem"
date: 2011-12-04
forum: Desktop Environments
---

### Post by isri on 2011-12-04
Hello,

I have problems with mounting some DVDs using my Ubuntu desktop (10.10). 

Last time I've bought 50 the same DVDs (Verbatim DVD+R) to make some space on my laptop drive (currently Mint 9). All of them were burned in the same way. All were burned fine.

Today I wanted to copy some data from those DVDs to my desktop and it appears I'm not able to mount them.

They are mounting with no errors on my laptop and two other desktops but on my main I'm getting:

```
[ 23:00:51 11-12-04 ]
 - %: /home> sudo mount /dev/sr0 /media/cd
mount: /dev/sr0: unknown device
zsh: exit 32    sudo mount /dev/sr0 /media/cd

[ 23:01:11 11-12-04 ]
 - %: /home> sudo mount /dev/sr0 /media/cd -t iso9660
mount: no medium found on /dev/sr0
zsh: exit 32    sudo mount /dev/sr0 /media/cd -t iso9660

[ 23:04:00 11-12-04 ]
 - %: /home> sudo mount /dev/sr0 /media/cd -t udf    
mount: no medium found on /dev/sr0
zsh: exit 32    sudo mount /dev/sr0 /media/cd -t udf

```I've tested about 10 from those 50 and get about 4 that are not working - the same way. Just on my desktop - all are working on other computers (Ubuntu, Mint, XP).

```
sudo hdparm -iI /dev/sr0

/dev/sr0:

 Model=ATAPI   iHAS122   8, FwRev=3L04, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


ATAPI CD-ROM, with removable media
    Model Number:       ATAPI   iHAS122   8                     
    Serial Number:      
    Firmware Revision:  3L04    
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    PACKET command feature set
       *    DEVICE_RESET command
       *    NOP cmd
       *    Mandatory FLUSH_CACHE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Host-initiated interface power management
       *    Phy event counters
            Device-initiated interface power management
       *    Software settings preservation

```

My DVD drive is rather fine - I've checked with some other DVDs (+R; -R; DL burned earlier or later) and CDs - working fine.

Has anyone any idea?

Thanks

---

### Post by moondoggy2 on 2012-04-07
Bump

---


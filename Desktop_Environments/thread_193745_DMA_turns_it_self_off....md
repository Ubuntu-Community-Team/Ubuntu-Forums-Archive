---
title: "DMA turns it self off..."
date: 2006-06-10
forum: Desktop Environments
---

### Post by someusernoob on 2006-06-10
Ok. 

HDA = 80GB EXT3 (WD 7200 8MB)
HDB =120GB NTFS/EXT3 (Maxtor 7200 8MB)

When i boot into Ubuntu this is what i get:
```

owner@PC1:~$ sudo hdparm -d /dev/hda /dev/hdb

/dev/hda:
 using_dma    =  1 (on)

/dev/hdb:
 using_dma    =  1 (on)

```

Then i go copy a large file (700MB) from hda to hdb, and when it is halfway there, it goes suddenly much much slower, and what i get is:
```

owner@PC1:~$ sudo hdparm -d /dev/hda /dev/hdb

/dev/hda:
 using_dma    =  0 (off)

/dev/hdb:
 using_dma    =  1 (on)

```

Ok, i know i can enable it by putting a 1 after de -d (-d1) but thats anoying since i cant walk away from my computer during the copy. It does not always happen, only about 50% of the time.

When i do this:
```

owner@PC1:~$ sudo hdparm -i /dev/hda /dev/hdb

/dev/hda:

 Model=WDC WD800JB-00JJA0, FwRev=05.01C05, SerialNo=WD-WMAM91382409
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=66
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode


/dev/hdb:

 Model=Maxtor 6Y120P0, FwRev=YAR41BW0, SerialNo=Y3NJTE6E
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=7936kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=240121728
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

```
i don't see anything strange?

This is my fstab file.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb5       /media/Data     ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
and as you can see, i do not mount my NTFS disk because i do not want to, nothing there to use on Linux.

I just did a fresh install, and the problem is not solved. I also changed my IDE cable just in case.

Anyone has any idea what i can do besides keeping my terminal open and enabling DMA the whole time? Or where to look for something that might be the problem?

---

### Post by someusernoob on 2006-06-10
I took a look in /var/log/messages and found errors!! lol

A little piece of the list:
```

Jun 10 18:44:03 PC1 kernel: [4295538.965000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jun 10 18:44:03 PC1 kernel: [4295538.965000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jun 10 18:44:03 PC1 kernel: [4295538.965000] ide: failed opcode was: unknown
Jun 10 18:44:03 PC1 kernel: [4295538.965000] hda: DMA disabled

```

I found on a Dutch forum ([click]("http://gathering.tweakers.net/forum/list_messages/751613///dma")) that it could be the IDE cable, the chipset or the hard disks itself. So first im gonna make sure it's not one of the hard disks.

Did some testing with the tools from the hard drive manufacturers and found luckely no errors. Then i changed my IDE cable again, but now with another one, an oldy, and guess, problem seems solved, so both IDE cables that were in my computer were "broken".... strange... But for the moment no errors and happy copying.... :D

---


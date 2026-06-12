---
title: "Inspiron 8100 slow.  Inappropriate ioctl for device"
date: 2007-07-14
forum: Dell  Ubuntu Support
---

### Post by gerryscat on 2007-07-14
I have installed 7.04 but it seems slow. I used to have XP on this system (1 Ghz Celeron/256 meg) and with a little tweaking was able to watch HD downloads. With Ubuntu the video is unwatchable.

I read (at [http://opensource.apress.com/article/65/command-line-gems-hdparm](http://opensource.apress.com/article/65/command-line-gems-hdparm)) I need to change my harddrive settings to enable DMA, but it doesn't work. My HD is terrible,  looks like it is running in 16 bit mode:

sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   282 MB in  2.01 seconds = 140.24 MB/sec
 Timing buffered disk reads:   24 MB in  3.03 seconds =   7.91 MB/sec

sudo hdparm /dev/sda 

/dev/sda:
 IO_support   =  0 (default 16-bit)

sudo hdparm -m16 /dev/sda

/dev/sda:
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device

 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 3648/255/63, sectors = 58605120, start = 0

sudo hdparm -i /dev/sda 

/dev/sda:

 Model=FUJITSU MHR2030AT                       , FwRev=30B8    , SerialNo=        NJ17T2212JMP
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?8?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=58605120
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 1:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

So, anybody know why I'm getting inappropriate ioctl for device, and how I get the appropriate one? How can I speed up my HD?  :(

thanks,
Gerry

---

### Post by rombel4u on 2007-07-14
i have the same problem on my inspiron 8600. i am using segate 7200 rpm pata drive and get the same message.

---

### Post by daln on 2008-07-04
1) remove all lines with 'ide-generic' from /etc/modules
2) add lines into /etc/init.r/bootmisc.sh :

modprobe ide-generic
modprobe ide-generic dma=1
hdparm -d1 /dev/YOUR_DISK_OR_DVDROM

3) reboot

For 8.04 realese you should edit '/etc/init.d/bootmisc.sh'
There is no init.r in 8.04 realese

---


---
title: "hdparm -v &amp; -t issues"
date: 2005-12-12
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-12
Hi all,
       Recently while reading a tech magazine, I came across this article which told me that one could change the hard disk parameters & improve the booting up as well as general work in Ubuntu 5.10 . Noob here, This is my output from running hdparm -v /dev/hda. The chipset I have is (Intel i845 GLM) & the drive is Samsung 80 GB PATA 133. It was also written in the article as well as the man page that manipulating drive settings can cause problems if the chipset is not supported or the drive doesn't support the setting fully.

Now my questions are :- 
1. Now how to know whether the chipset is being supported or not as well what drive settings are fully supported. 

when giving hdparm -t /dev/hda it gives 
          /dev/hda :
   Timing buffered disk reads: 12 MB in 3.21 seconds=3.74 MB/sec

Now I know this can be increased quite dramatically without endangering the hdd but not sure how to go about configuring things, can anyone help. Below is the hdparm -v settings as of right now, the only change I made was the -d1 flag till now.

shirishag75@ubuntu:~$ hdparm -v /dev/hda
/dev/hda: Permission denied
shirishag75@ubuntu:~$ sudo hdparm -v /dev/hda
Password:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156368016, start = 0

---

### Post by hod139 on 2005-12-16
Here is a decent howto for[ tuning up your hard disks using hdparm]("http://usalug.org/phpBB2/viewtopic.php?p=33142")

---

### Post by limit223 on 2005-12-19
Amazing improvement ...WOW!!

Just  for my /dev/hdb that looks almost the same with the one in the guide:

~$hdparm -i /dev/hdb
/dev/hdb:

 Model=WDC WD1200JB-32EVA0, FwRev=15.05R15, SerialNo=WD-WMAEK1196032
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

I add a line at the end of the script before 'exit' in /etc/init.d/hdparm:
hdparm -d1 -A1 -m16 -u1 -a64 -X69 -S180 /dev/hdb

And boot was ...half of the normal time (much shorter than all other used tips and hacks)....incredible!!

---


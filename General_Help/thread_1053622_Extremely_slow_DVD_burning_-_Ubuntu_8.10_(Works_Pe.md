---
title: "Extremely slow DVD burning - Ubuntu 8.10 (Works Perfect in Windows)"
date: 2009-01-28
forum: General Help
---

### Post by bcairns on 2009-01-28
I have spent literally weeks searching Google and other forums before posting this...

I am new to linux but not new to computers.
(Looking to get away from Windows)

Installed Ubuntu 8.10
Everything seems pretty good, video, sound, everything but burning a DVD.

Can read DVDs / CDs - but when I attempt to burn a DVD it burns at less then 1x saying it will take about 3 hours to an hour to burn.

**Please note everything works perfectly in windows **- I can burn DVDs all day in windows and a typical 4gb ISO takes about 8 minutes.

I have tried a few things that I have found in other forums and nothing so far has worked.

Pretty much this is what I have done:
Upgraded the Bios
Upgraded the DVD Drive Firmware
Set the DVD to Slave on the Secondary Channel
blacklisted the pata_atiixp driver
A ton of commands that I found in other forums (and nothing worked so far)

My setup is as follows...

**Motherboard**
ASUS A8R32-MVP Deluxe Socket 939 ATI CrossFire Radeon XPRESS 3200 ATX AMD Motherboard

**CPU**
AMD Athlon 64 X2 4800+ Toledo 2000MHz

**Ram**
4GB Corsair 184-Pin DDR SDRAM

**Drives:**
150 GB WD SATA Raptor (Windows XP SP2)
250 GB WD SATA (Storage)
250 GB WD SATA (Storage)
1 TB WD SATA (Ubuntu 8.10)

**DVD / CD**
Samsung SH-S162L - ATAPI: TSSTcorpCD/DVDW SH-S162L, TS01, max UDMA/33

**Some additional notes...**

One thing I thought was that the DVD is ther master on the primary cable, and linux might be getting confused by two masters, so I moved it to the slave on the second channel. Same results, still burns slow, but now Ubuntu gets the correct speed in device manager.

**Ubuntu is detecting the DVD drive as:**

> bcairns@bcairns-ubuntu:~$ hdparm -i /dev/scd0

/dev/scd0:

 Model=TSSTcorpCD/DVDW SH-S162L                , FwRev=TS08    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

**When I do a "dmesg | grep ata" I get**
> 
[   15.455409] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   15.804414] ata8.01: ATAPI: TSSTcorpCD/DVDW SH-S162L, TS08, max UDMA/33
[   15.804423] ata8.01: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[   15.804426] ata8.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[   15.844360] ata8.01: configured for UDMA/33

My first thought was the DMA settings are not right, but any attempt to control them seems to fail horribly...

> bcairns@bcairns-ubuntu:~$ sudo hdparm -d1 -c1 /dev/scd0

/dev/scd0:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default) 
 HDIO_GET_DMA failed: Inappropriate ioctl for device


In the Bios the disk settings are set to Auto, I can change them bu have no idea what to set them to or if that would even help.

There are other people having this problem but the only resolution seems to be boot into windows to burn DVDs. Some people get this fixed but most don't seem to.

**Here are some of the links I found relevant while searching.**
[http://ubuntuforums.org/showthread.php?t=808490](http://ubuntuforums.org/showthread.php?t=808490) 
[http://ubuntuforums.org/showthread.php?t=767449&highlight=slow+dvd&page=2](http://ubuntuforums.org/showthread.php?t=767449&highlight=slow+dvd&page=2)
[http://ubuntuforums.org/showthread.php?p=4615284](http://ubuntuforums.org/showthread.php?p=4615284)
[http://ubuntuforums.org/showthread.php?t=128721&page=9](http://ubuntuforums.org/showthread.php?t=128721&page=9)
[http://ubuntuforums.org/showthread.php?t=128721&page=11](http://ubuntuforums.org/showthread.php?t=128721&page=11)
[http://ubuntuforums.org/archive/index.php/t-214968.html](http://ubuntuforums.org/archive/index.php/t-214968.html)
[http://www.debianhelp.co.uk/burningdvd.htm](http://www.debianhelp.co.uk/burningdvd.htm)

One thing that really bothers me is that everything is fine in windows, I have zero hardware issues. so i decided to try other live CDs and was shocked to have issues...

**Fedora 10**
Can not boot to live CD, instead it gives me a Machine Check Exemption: CPU 1 Kernel Panic Can not Syncing 00000000000000004

**Open Suse 11.1**
I get the same Kernel Panic error in normal boot, but if I boot using the failsafe setting it does get me to boot and into an active desktop.

I read up on MCE and found they are hardware issues, but Ubuntu and Windows work fine and Suse loads in fail safe mode.

:KS:KS:KS I am *REALLY* hoping that someone out there has run into this before and can at the very least point me in the right direction :p

---

### Post by exploder on 2009-01-28
Try removing the current version of Brasero and install the newer version form here.

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

---

### Post by frogotronic on 2009-01-28
Firstly install the medibuntu repos and get all the libraries to read DVDs, then I use K3B (install via synaptic) as my burning program - its awesome.

---

### Post by bcairns on 2009-01-28
> **exploder said:**
> Try removing the current version of Brasero and install the newer version form here.

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

Same results :(

Burn speed = 948kb (0.7x) estimated time ranges from 1:35:25 to 3:25:00

A side note...

The system gets laggy - mouse jerks, things of that nature.

---

### Post by bcairns on 2009-01-29
So far nothing seems to fix this. I will try medibuntu and the ideas I got in private messages - will keep you posted and thank you very much for responding.

:D

---

### Post by bcairns on 2009-01-30
nothing works so far any other suggestions?

---


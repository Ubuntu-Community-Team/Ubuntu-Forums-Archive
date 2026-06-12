---
title: "x16 DVD burner but only burning at x0.20?!!"
date: 2006-06-06
forum: Desktop Environments
---

### Post by harty83 on 2006-06-06
Hello,

I have a x16 DVD burner but the fastest I've seen it burn is x0.90.  I'm using K3b to burn Verbatim DVD-Rs.  Any suggestions on why this is and how do I get it to burn at the rate it is suppose to?

Thanks!

---

### Post by Patsoe on 2006-06-06
Have you checked if it is in DMA mode? You can check this with the command "hdparm /dev/<your drive>". For example, I would type "hdparm /dev/hdc" to query my CDRW drive.

---

### Post by harty83 on 2006-06-06
I already have it enabled but am still getting the slow speed.

```
 using_dma    =  1 (on)

```

---

### Post by chrx on 2006-10-09
my dvdburner (benq dw1670) is also burning very slow. a dvd took me about 90 min.

ive checked dma.

chriz@chriz-desktop:~$ sudo hdparm -d1 /dev/hdd
Password:

/dev/hdd:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

Any advise?:confused:

---

### Post by GuiGuy on 2006-10-24
> **chrx said:**
> my dvdburner (benq dw1670) is also burning very slow. a dvd took me about 90 min.

ive checked dma.

chriz@chriz-desktop:~$ sudo hdparm -d1 /dev/hdd
Password:

/dev/hdd:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
:confused:

Did you manage to solve this?

---

### Post by chrx on 2006-11-01
thanxs for the reply.
well it was the dma setting, sometimes its on, sometimes its off..

---

### Post by GuiGuy on 2006-11-01
> **chrx said:**
> thanxs for the reply.
well it was the dma setting, sometimes its on, sometimes its off..

I've given up. I've put the 16X pioneer burner into my Windows box and put an old 4X liteon into the Linux machine, which no matter what I do, will not go faster than 1.7X speed :confused: 

It shouldn't be this difficult!

 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

= 1.7x max burning speed :(

---

### Post by otherdave on 2006-11-01
I have no idea if this will help anyone, OR if you want to recompile your kernel...

I recently switched from Gentoo linux (it's the distribution where you compile EVERYTHING in case you're not familiar with it). 

I recently bought a new DVD writer and it was insanely slow. While researching it, I found this thread in the Gentoo forums:
[ read it here](http://forums.gentoo.org/viewtopic-t-292252-highlight-.html).

I'm 'otherdave' in that forum as well. The fix for me was to disable Generic IDE in the kernel.

---

### Post by GuiGuy on 2006-11-03
> **otherdave said:**
> 
I recently bought a new DVD writer and it was insanely slow. While researching it, I found this thread in the Gentoo forums:
[ read it here](http://forums.gentoo.org/viewtopic-t-292252-highlight-.html).



Thanks for that, but telling me to 'recompile the kernel' is like asking me to plan a trip to the moon. I just want an OS that works. In my case Linux doesn't when it comes to multimedia stuff.


regards

---

### Post by cbxbiker61 on 2006-11-17
I had the exact same problem when using dvd+rw-tools.  The solution  for me was to simply use cdrecord to burn iso images.  It flies with my Samsung SH-S182D at 18x using Verbatim 16X dvd+r.  The latest version of cdrecord works great burning DVD's regardless of what you may have read elsewhere.

k3b uses growisofs which is part of dvd+rw-tools, so unfortunately i'm doing my burns from the command line with cdrecord, but i don't mind when I get flawless burns.

---

### Post by thocar on 2007-02-12
> **cbxbiker61 said:**
> I had the exact same problem when using dvd+rw-tools.  The solution  for me was to simply use cdrecord to burn iso images.  It flies with my Samsung SH-S182D at 18x using Verbatim 16X dvd+r.  The latest version of cdrecord works great burning DVD's regardless of what you may have read elsewhere.

k3b uses growisofs which is part of dvd+rw-tools, so unfortunately i'm doing my burns from the command line with cdrecord, but i don't mind when I get flawless burns.

I bought the same DVD Writer but it is very slow to burn too, can you post the result of the following commands to help us solve the problem

$ cdrecord -dev=ATA -scanbus
$ cdrecord -dev=ATAPI -scanbus
# X identifies your DVD-Writer
$ cat /proc/ide/hdX/driver
$ hdparm /dev/hdX
$ hdparm -i /dev/hdX
# insert a DVD
$ hdparm -tT /dev/hdX
$ grep hdX /etc/fstab
$ uname -a
$ "the command you use to burn a DVD"

and attach your kernel config file (/usr/src/linux/.config)

Thanks a lot

---

### Post by minijoe on 2007-03-07
ok... looks like I am not alone on this issue(I almost RMAed my Samsung DVD burner)

thocar,

Here is my out put from the commands recommended:


///~$ sudo cdrecord -dev=ATAPI -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: No such file or directory. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
joe@ubuntu2000:~$ cls

joe@ubuntu2000:~$ cdrecord -dev=ATA -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) 'TSSTcorp' 'CD/DVDW SH-S182M' 'SB03' Removable CD-ROM
cdrecord: Warning: controller returns wrong size for CD capabilities page.
        1,1,0   101) 'LG      ' 'CD-ROM CRD-8521B' '1.04' Removable CD-ROM
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *


///$ cdrecord -dev=ATAPI -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: No such file or directory. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

////~$ cat /proc/ide/hdc/driver
ide-cdrom version 4.61

///$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


~$ hdparm -i /dev/hdc

/dev/hdc:

 Model=TSSTcorpCD/DVDW SH-S182M, FwRev=SB03, SerialNo=
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


~$ sudo hdparm -tT /dev/hdc
Password:

/dev/hdc:
 Timing cached reads:   1084 MB in  2.00 seconds = 541.70 MB/sec
BLKFLSBUF failed: Function not implemented
 Timing buffered disk reads:   58 MB in  3.06 seconds =  18.94 MB/sec
BLKFLSBUF failed: Function not implemented


~$ grep hdc /etc/fstab
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

~$ uname -a
Linux ubuntu2000 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

*** I am using GnomeBaker to burn DVD ISO images

Thanks for helping out here. Hope my information can lead to a solution.

---


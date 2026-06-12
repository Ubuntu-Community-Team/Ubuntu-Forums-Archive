---
title: "File transfers extremely slow"
date: 2009-02-18
forum: General Help
---

### Post by jamesnmandy on 2009-02-18
Hello all, 

I am new to this so if there's important data you need added to this post please say so.

I just installed Ubuntu 8.10 fresh and clean last night.  I tried to do two things this morning for the first time.

A. transfer (copy) a 7Gb file from my external USB HDD to my desktop to work with it and it is running dreadfully slow, to the point it is completely unacceptable.  Windows 7 did this in 20 minutes tops, Ubuntu is taking roughly 2 hours to do the same task on the same exact machine.

B. unrar the same 7Gb multi part file....same thing, slow as if time stands still, took 8 minutes to complete under Windows 7 with WinRar, now looks to be taking a couple hours..........

What am I missing?  What can I do?  I am getting a 1 megabyte per second transfer speed, which leads me to believe the USB ports are somehow gimped to USB 1 speed.  The external drive is in an Antec MX-100 enclosure which has a 750Gb SATA drive in it plugged of course into the enclosure's SATA->USB host card, then USB cable to PC.  It is formatted Fat32 which must remain for ability to be accessible on my Xbox 360 for watching movies and listening to music.  Perhaps there is a USB 2.0 driver that I am missing?  I don't know how to tell.  The enclosure was listed as being Linux compatible so it's on the approved list I would imagine as far as hardware compatibility is concerned.

When I go into the system monitor it shows the CPU and memory barely being used, system is just as snappy as usual so the system is not out of resources or bogged down.....

System is a Shuttle ST62K, ATI 9100IGP chipset on motherboard, using onboard audio and video, internal IDE 80GB HDD......P4 3.0E cpu, 2 Gb's of ram.....not a power house but certainly did not expect things that would have taken less than 30 minutes combined on a bloated Windows OS to take 4 to 5 hours on Linux.......
Help

---

### Post by Slim Odds on 2009-02-18
use hdparm to make sure that DMA is enabled.

---

### Post by jamesnmandy on 2009-02-18
could you elaborate please?  when you say "use hdparm" how do i "use" it?  i know it's a command line...or terminal command, but exactly how do i type in the command, any strings, etc...?

---

### Post by Slim Odds on 2009-02-18
I'm little rusty....

```
sudo hdparm /dev/{your device here}
```

... will give you some info about your drive.

"man hdparm" for further details

---

### Post by jamesnmandy on 2009-02-18
```
/dev/sdb1:
 Timing cached reads:     2 MB in  2.15 seconds = 951.14 kB/sec
 Timing buffered disk reads:    4 MB in  4.30 seconds = 953.50 kB/sec
jamesnmandy@jamesnmandy-desktop:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   1438 MB in  2.00 seconds = 719.12 MB/sec
 Timing buffered disk reads:  168 MB in  3.00 seconds =  55.92 MB/sec
```

where sdb1 is my USB attached 750Gb HDD and sda1 is my IDE 80Gb internal HDD

---

### Post by Slim Odds on 2009-02-18
> **jamesnmandy said:**
> 
jamesnmandy@jamesnmandy-desktop:~$ sudo hdparm -tT /dev/sda1


Run it without the -tT so that it will tell you what the current settings are.

---

### Post by jamesnmandy on 2009-02-19
Ok, there was one other partition actually if i understand correctly, sda1 being boot, sda2 being the working directory (the remainder of the 80Gb HDD that Ubuntu is installed on, and sdb1 being the external USB FAT32 750GB HDD

```
/dev/sda1:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9729/255/63, sectors = 149838192, start = 63
```

```

/dev/sda2:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9729/255/63, sectors = 2, start = 149838255
```

```
/dev/sdb1:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 25665/255/63, sectors = 1464983352, start = 63
```

***also found out how to use tags to see how the disks are being used and capabilities, results below

```
/dev/sda1:

 Model=WDC WD800JB-00JJC0                      , FwRev=05.01C05, SerialNo=     WD-WCAM94959275
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=66
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode
```

```
/dev/sda2:

 Model=WDC WD800JB-00JJC0                      , FwRev=05.01C05, SerialNo=     WD-WCAM94959275
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=66
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode
```

```
/dev/sdb1:
 HDIO_GET_IDENTITY failed: Invalid argument
```

---

### Post by jamesnmandy on 2009-02-20
is this going to end well?  i wonder....

i went ahead and installed wine and winrar, that helped the unraring of large files go much much quickly, maybe 15 minutes tops for something that was taking the natively installed archive program close to two hours

i think the issues are two, one is a USB device transfer speed issue, the other is software.....because it's just wrong for a windows app running under wine to be running multitudes faster than the native program.....but the file transfers......

again, on the windows install, the same process that takes hours on this Ubuntu machine takes only minutes, and a windows app running in wine cut the other time way down....i see a pattern....i thought linux was supposed to be less harsh on resources and therefore should be faster or at least as fast right?

---

### Post by jerome1232 on 2009-02-20
> **jamesnmandy said:**
> ```
/dev/sdb1:
 Timing cached reads:     2 MB in  2.15 seconds = 951.14 kB/sec
 Timing buffered disk reads:    4 MB in  4.30 seconds = 953.50 kB/sec
jamesnmandy@jamesnmandy-desktop:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   1438 MB in  2.00 seconds = 719.12 MB/sec
 Timing buffered disk reads:  168 MB in  3.00 seconds =  55.92 MB/sec
```

where sdb1 is my USB attached 750Gb HDD and sda1 is my IDE 80Gb internal HDD

Just an observation but sdb sure looks like it's going at full-speed usb (1.1), do you have any hi-speed (2.0) usb ports?

---

### Post by jamesnmandy on 2009-02-20
the same drive is in the same USB port using the same cable...nothing was changed but the operating system.....thats what i am looking into now, how to somehow enable USB 2.0 support on my system, it worked fine in windows, i am sure there will eb a solution here somewhere

but what about the rar issue?  why would that happen?

---

### Post by theozzlives on 2009-02-20
TAR is native to Linux, but never had any problems with RAR files. I only get slow speeds  on USB  when I use  my older  machine with  USB 1.1.

---

### Post by jamesnmandy on 2009-02-20
thats what i dont get.....

Ubuntu 8.10 using Archive Manager as installed fresh yields about a 2 hour wait for it to unrar a 7GB file, this is with the file on the local HDD

Windows 7 using Winrar would do the same job witht he same file in about 8-10 minutes  

Ubuntu 8.10 + Wine + Winrar yields me about a 12-15 minute job for the same exact file, again on the local HDD, slower than windows, but WAY faster than using Archive Manager

so what gives?

this is an entire different issue than the USB HDD transfer speed issue everyone is having...

---

### Post by jamesnmandy on 2009-02-25
can i get some sort of official reply, a link to an official response like a "we know there's an issue, "we're working on it" or something other than the many threads on the same topic appearing to be ignored?...something?

i checked the .....i dunno what it's called, the official "known bug list" found here [http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825) and this issue is still not acknowledged!  yet, there are thread upon thread, user upon user, with different hardware configs with two things in common.

A. USB speeds gimped to 1.0 and 

B. Ubuntu installed in the last few official releases

---

### Post by Rekoil on 2009-03-26
I'm having the exact same problem unraring files as jamesnmandy, I'd love an official answer as well. Don't know if my system is suffering from the USB problems as well because I don't use USB with it (it's a server).

Unraring files which take 6 minutes tops in winrar via wine will take at least a half hour using unrar.

And for the record, the same thing is happening with Debian lenny, maybe that has something to do with it? The last OS I ran on the server which wasn't suffering from this problem was Debian etch. Don't think it has to do with the unrar/rar package and don't think it affects all systems. My server has an AMD Athlon 64 x2 4200+ processor with 1gb of ram installed.

---


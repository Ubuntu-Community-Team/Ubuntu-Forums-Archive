---
title: "Very Slow eSata performanace"
date: 2009-02-02
forum: General Help
---

### Post by cbonilla on 2009-02-02
System:
Heron 8.04 server
Dell poweredge 2650, twin xeon proceessors (with all bios and driver updates)2GB RAM

Twin SCSI drives set up as RAID 1. These are small drives holding only Ubuntu. No problem here

Silicon Image 3124 RAID controller with two Seagate 750GB eSata 2 drives set up as RAID 1 using Linux for RAID since the SI controller produces only fake raid. Instead drives are configured using MDADM as Linux Raid. Ubuntu sees the drives as a RAID 1, no problem with that

I&#8217;ve been disappointed with access speed on the eSata drives (jumper removed to allow operation at 300 and not 150). Today I did a test and saved an Excel file on an old slow Windows XP box with ATA drives on my gigabit home network. File opened from a vista machine in a snap. But when I try to open the same file from the same vista box off the PowerEdge it took 5-6 seconds.

Any idea what is going on? FYI, when I look at the eSata drives WebAdm on the Ubuntu box identifies them as SCSI and not eSata drives

Here are the hparm specs on one of the eSata drive
/dev/sdb:
 Timing cached reads:   678 MB in  2.00 seconds = 338.35 MB/sec
 Timing buffered disk reads:  136 MB in  3.02 seconds =  44.97 MB/sec

/dev/sdb:

 Model=ST3750640AS                             , FwRev=3.AAE   , SerialNo=            3QD0E6T5
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

Thanks for your help

---

### Post by cbonilla on 2009-02-05
I hope it isn't rude to bump myself back to the top

Carlos

---

### Post by all-beans on 2009-02-07
I'm having a similar problem with 8.10 Intrepid. Comparing 4 machines I have, 1 with Hardy Heron (8.04), 1 with Dapper Drake (6.06) and 2 with Intrepid (8.10).

All 4 machines have similar hardware with 3 SATA 7200 rpm ~250GB drives, dual core CPU x86, 2 GB mem.  The Hardy Heron and Dapper Drake machines seem to have excellent performance. The 2 Intrepid machines are sluggish when it comes to file system access. I know this because all 4 are running vmware servers (same version, 1.06) with XpPro SP3 guests. When I remote desktop to XP accessing NTFS files on these guests, they are fast with the 8.04 and 6.06 but very very slow with 8.10. 

Some may suggest this is related to the mush larger number of processes on Intrepid since GNOME (GUI) and all are running, or at least loaded and are not present on Hardy and Dapper. Not so I tested this by looking at CPU load on each machine and although Intrepid has a slightly higher load I don't believe it to be high enough to explain the huge performance difference.

Does someone have any idea of what the differences are between the mdadm (raid support software) of the above Ubuntu releases are?

I suspect the mdadm package on Intrepid has some problems. I also remember that I had to download the a different release to get raid support with Intrepid. the standard install (GUI) version did not support raid or mdadm.

Thanks in advance.

P.S. My hat goes off the the Ubuntu team, excellent OS. Good job and keep up the good work.

---

### Post by cbonilla on 2009-02-07
Well I just upgraded from Heron to 8.10 hoping to fix the problem. No difference

---

### Post by all-beans on 2009-02-07
What version of mdadm are you running?
I'm running 

user@hardy:~# mdadm --version
mdadm - v1.12.0 - 14 June 2005

and

user@intrepid:~# mdadm --version
mdadm - v2.6.7 - 6th June 2008

Version v1.12.0 has much better performance.

---

### Post by cbonilla on 2009-02-07
I'm running 2.6.7 June '08

My next effort is going to be to investigate whether I have a Ubuntu I/O problem or a Ubuntu network problem, although the read out from both the light on the ethernet port and the output from a (forgotten) command I ran showed gigabit connection. 

I think the routine I need to run is iperf to check and see if that is the bottleneck.

---

### Post by cbonilla on 2009-02-18
Here are the iperf/jperf results from my system. Wired gigabit network. PowerEdge 2650 running 8.10


Here is the jperf/iperf result from a slow XP box with a gigabit adapter to the poweredge server. This is a wired gigabit network

[1912] local 192.168.1.3 port 2222 connected with 192.168.1.252 port 5001
[ ID] Interval Transfer Bandwidth
[1912] 0.0- 1.0 sec 47088 KBytes 385745 Kbits/sec
[1912] 1.0- 2.0 sec 55288 KBytes 452919 Kbits/sec
[1912] 2.0- 3.0 sec 55024 KBytes 450757 Kbits/sec
[1912] 3.0- 4.0 sec 54896 KBytes 449708 Kbits/sec
[1912] 4.0- 5.0 sec 54976 KBytes 450363 Kbits/sec
[1912] 5.0- 6.0 sec 55192 KBytes 452133 Kbits/sec
[1912] 6.0- 7.0 sec 54840 KBytes 449249 Kbits/sec
[1912] 7.0- 8.0 sec 54936 KBytes 450036 Kbits/sec
[1912] 8.0- 9.0 sec 55040 KBytes 450888 Kbits/sec
[1912] 9.0-10.0 sec 55400 KBytes 453837 Kbits/sec
[1912] 0.0-10.0 sec 542688 KBytes 443876 Kbits/sec

and here is the result from a Vista box to the samer PowerEdge Server

108] local 192.168.1.2 port 52646 connected with 192.168.1.252 port 5001
[ ID] Interval Transfer Bandwidth
[108] 0.0- 1.0 sec 30688 KBytes 251396 Kbits/sec
[108] 1.0- 2.0 sec 32096 KBytes 262930 Kbits/sec
[108] 2.0- 3.0 sec 33344 KBytes 273154 Kbits/sec
[108] 3.0- 4.0 sec 32528 KBytes 266469 Kbits/sec
[108] 4.0- 5.0 sec 33200 KBytes 271974 Kbits/sec
[108] 5.0- 6.0 sec 33040 KBytes 270664 Kbits/sec
[108] 6.0- 7.0 sec 32752 KBytes 268304 Kbits/sec
[108] 7.0- 8.0 sec 33968 KBytes 278266 Kbits/sec
[108] 8.0- 9.0 sec 32872 KBytes 269287 Kbits/sec
[108] 9.0-10.0 sec 32464 KBytes 265945 Kbits/sec
[108] 0.0-10.0 sec 326960 KBytes 267712 Kbits/sec

What I'm trying to close in on is whether my slow file transfer times are a network bottleneck or a disk I/O problem on the PowerEdge server.

Thoughts?

Thanks, Carlos

---


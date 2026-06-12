---
title: "DVD burning problems in 8.10"
date: 2009-04-21
forum: General Help
---

### Post by tdreyer1 on 2009-04-21
I have been having CD and DVD burning problems since I upgraded to Ubuntu 8.10. Whether I use wodim, brasero, or the built in iso-writer in nautilus, the same thing happens: The burn will start, then freeze. 
In wodim, I get the following output:
```
tim@tim-desktop:~/isos$ sudo wodim -v -dummy dev=/dev/dvdrw speed=4 ubuntu-9.04-rc-dvd-i386.iso 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/dvdrw'
devname: '/dev/dvdrw'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PLEXTOR '
Identification : 'DVDR   PX-716AL '
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 6291456 = 6144 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 42442 kB/s 241x CD 30x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data  4344 MB        
Total size:     4989 MB (494:21.10) = 2224583 sectors
Lout start:     4990 MB (494:23/08) = 2224583 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 73913
Speed set to 5540 KB/s
Starting to write CD/DVD at speed   4.0 in dummy unknown mode for single session.
Last chance to quit, starting dummy write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Track 01:   22 of 4344 MB written (fifo 100%) [buf  98%]   4.1x.wodim: faio_wait_on_buffer for writer timed out.

```

Then it just freezes. Help?

---

### Post by khelben1979 on 2009-04-21
First I would like to recommend that you upgrade the firmware in your dvd writer. Go to [Plextors homepage]("http://www.plextor.com/") to get it.

Try [k3b]("http://en.wikipedia.org/wiki/K3b") instead (check out the link for more information about the program)

```
sudo apt-get install k3b
```
to install it.

---

### Post by tdreyer1 on 2009-04-21
> **khelben1979 said:**
> First I would like to recommend that you upgrade the firmware in your dvd writer. Go to [Plextors homepage]("http://www.plextor.com/") to get it.

Try [k3b]("http://en.wikipedia.org/wiki/K3b") instead (check out the link for more information about the program)

```
sudo apt-get install k3b
```
to install it.

I installed the latest updates about a week ago.

Using K3B has the same problems: Freezes when it has written only about 9 MB and requires a reboot to use the drive any more.

---

### Post by khelben1979 on 2009-04-21
I have read about this problem before on this forum, and it was solved by using another brand of discs to burn to. It has been said that Verbatim discs works good.

I wonder if you really have all the required packages in your system which is needed for cd-r/dvd-r burning.. :-k

What brand are you currently using?

---

### Post by tdreyer1 on 2009-04-21
> **khelben1979 said:**
> I have read about this problem before on this forum, and it was solved by using another brand of discs to burn to. It has been said that Verbatim discs works good.
...
What brand are you currently using?

Imation like [those found here]("http://www.quill.com/imation-dvd-r-discs/cbk/23060.html").

---

### Post by tdreyer1 on 2009-04-21
> **tdreyer1 said:**
> Imation like [those found here]("http://www.quill.com/imation-dvd-r-discs/cbk/23060.html").

Though I have never had a problem with this brand until 8.10, and windows programs like them fine. As such, I would like to find another fix other than buying another media, if possible.

---

### Post by tdreyer1 on 2009-04-25
bump:(

---


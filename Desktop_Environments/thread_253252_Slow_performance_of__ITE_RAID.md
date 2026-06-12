---
title: "Slow performance of  ITE RAID"
date: 2006-09-08
forum: Desktop Environments
---

### Post by canter690 on 2006-09-08
Hi

I have a giga-byte 8knxp motherboard with an integrated ITE RAID controller.  There are two 120GB drives connected and configured as a RAID-0.  I can see and mount the filesystem with no errors.

checked performance with the following command

```
sudo hdparm -t /dev/hdi1

/dev/hdi1:
 Timing buffered disk reads:   10 MB in  3.58 seconds =   2.80 MB/sec
```

Other posts indicated that I needed a driver for the raid. I have checked and the it821x driver is loaded as is the piix driver.

How do I improve the performance to this disk ?

---

### Post by canter690 on 2006-09-12
Anyone ?:frown:

---

### Post by canter690 on 2006-09-13
Bump

---

### Post by HAARP on 2006-09-13
Is DMA enabled?

You can check by typing **sudo hdparm /dev/hdi**

---

### Post by canter690 on 2006-09-14
Hey Haarp

Thanks for responding.  Was thinking this question was just way too hard for anyone to solve.

In response to your question the answer is NO - DMA is not enabled and I can not get it enabled.

```
sudo hdparm -d1 /dev/hdi1
  
/dev/hdi1:  
setting using_dma to 1 (on)  
HDIO_SET_DMA failed: Invalid argument  
using_dma    =  0 (off) 
```

So where to from here ?

---

### Post by HAARP on 2006-09-14
That's the problem. Without DMA, it will be slow as hell.
However, I can't tell you how to fix this. hdparm doesn't seem to be able to enable DMA, which sounds like a driver or hardware issue. Are you using a 80-pin data cable for the drives?

---

### Post by canter690 on 2006-09-14
I believe its an standard 80 pin flat ribbon cable.  Definatley not a SATA cable.  Point to note is that this H/W worked fine under WinXp so I do expect its a driver issue but I was of the understanding the the 2.6.15 kernel had the ITE8212 driver in it, so I shouldn't have seen a problem.  

I guess I would be interested in hearding if anyone else with the ITE8212 Raid subsystem has their DMA working. Anyone ?

---

### Post by jkounis on 2007-01-20
I had exactly the same problem as you describe. "hdparm -t /dev/hda1" revealed a transfer rate of less than 2 MB/s. I tried everything finally came across the following:

"hdparm -d1 /dev/hda1" did not work

"hdparm -d /dev/hda"  _did_ work. 

Once I typed this, my transfer rate jumped from 2MB/s to 85 MB/s. Alternatively, you can edit /etc/hdparm.conf to include the following lines:

/dev/hda {
        dma = on
}

---

### Post by Xenner on 2007-04-15
i am having the exact same problems and none of these solutions seem to work for me

---

### Post by jocko on 2007-04-15
I'm also getting the same problem. I have one drive connected to an nvidia nforce (P)ATA100 interface, one to an ite8212 raid chipset (running as (P)ATA133) and one connected to an Sil3112 SATA chipset.
These used to get designated /dev/hde, /devhdc and /dev/sda respectively on every boot.
A few weeks ago I upgraded from edgy to feisty (clean install from a herd 5 cd) and everything worked fine.
A kernel update (don't know which) caused the drive designations on the two ATA interfaces to be randomly assigned either one of hda, hdc, hde and hdg on each boot, and I noticed the system would become extremely slow whenever it tried to read/write on the disk on the ite controller (unraring a 750 Mb archive would take an hour or more instead of one minute or less, and the rest of the system would be almost unresponsive).
hdparm -t reports 1.75 Mb/s buffered disk reads (was around 50 Mb/s before).

I could fix this by enabling dma and 32 bit I/O support by adding hdparm commands for all /dev/hdX devices in /etc/hdparm.conf.
Now after a few more kernel updates (currently 2.6.20-15-generic) all drives are designated /dev/sdX, and hdparm apparently doesn't work anymore:

```

sudo hdparm -d1 /dev/sdb
/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

I know of no way to solve this (other than moving the cable to the slower nforce ata interface).

---

### Post by straficchio on 2007-04-23
Hi all,

sorry to be OT but you guys seem to be the only I could find using a ITE raid 8212 on Ubuntu.
I have a 7.04 installed and it doesn't seem to be any driver for this controller on my installation.
Is there anything you downloaded from repositories or you got the source code of the driver to compile?

Thank you for any suggestion,
Straficchio.

---

### Post by jocko on 2007-04-26
> **straficchio said:**
> Hi all,

sorry to be OT but you guys seem to be the only I could find using a ITE raid 8212 on Ubuntu.
I have a 7.04 installed and it doesn't seem to be any driver for this controller on my installation.
Is there anything you downloaded from repositories or you got the source code of the driver to compile?

Thank you for any suggestion,
Straficchio.

The name of the driver is pata_it821x and it is included in the kernel.

---

### Post by SergeiFranco on 2007-05-12
I have exactly same problem in Feisty, I cannot fix it by setting to DMA because Feisty using sdx device name (all harddrives are described as scsi).
The performance is terribly slow (un-usable).
I have been searching how to enable DMA on sdx device, so far no luck.
here is what I found so far:
[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636)

---


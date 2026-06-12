---
title: "Very slow CD burning"
date: 2006-07-13
forum: Desktop Environments
---

### Post by sprocket87 on 2006-07-13
I have a Lite On external USB CD/DVD-RW drive, capable of 52x CD-R burning. Every time I burn an audio disc in Linux it only achieves about 3x.

I've tried 3 apps in Ubuntu 6.06 so far: k3b, gnomebake, and bonfire. All of them get knocked back to 3x. Another odd thing is that I have to run all of them using sudo priveleges or else it won't find the external drive (/mnt/sd0 or something?). 

I can acheive 48x in any Windows burning app (Nero, ONES, CDBurnerXP, etc) with this burner with the same media (48x Memorex), for what it's worth. FYI this is on a Gateway M460XL laptop, 2GHz Pentium M, 2GB RAM.

I read something about enabling DMA but I don't know how to do that. Thanks!

---

### Post by Bossieman on 2006-07-13
Here is a guide for you.
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by sprocket87 on 2006-07-13
> **Bossieman said:**
> Here is a guide for you.
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

Hmm okay thanks for the link. I think my external CD drive is /dev/scd0 - is that right? How can I confirm this? It doesn't show up in /etc/fstab.

Assuming it *is* /dev/scd0, I went ahead and ran hdparm as follows:

$ sudo hdparm /dev/scd0

/dev/scd0:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

I'm wondering if I should try the command to enable DMA...

---

### Post by sprocket87 on 2006-07-13
Ok, went ahead and tried:

$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument

So no dice on that one...

---

### Post by Bossieman on 2006-07-13
What is the output of this command?
```

sudo hdparm /dev/cdrom

```

---

### Post by cptnapalm on 2006-07-13
hdparm can't change setting on scsi style devices, which includes SATA, as far as I know.  While there is a sdparm, it does not have the functionality of hdparm.

Since the OS is listing it as scd0, that means that SATA is enbabled in the kernel.  I wonder if the problem is that the device itself is IDE, just with a SATA interface... that would explain why many people have this problem.

While a laptop, there is this guide which may be of use: [http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_cdrw_dvdrw_multi_burner](http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_cdrw_dvdrw_multi_burner)

I'm at work, so I'll get back if I can.

---

### Post by cptnapalm on 2006-07-13
actually, the output of "sudo hdparm -tT /dev/scd0" might be handy as well; I think having a disc in the drive might be required.

---

### Post by sprocket87 on 2006-07-13
> **Bossieman said:**
> What is the output of this command?
```

sudo hdparm /dev/cdrom

```

$ sudo hdparm /dev/cdrom
Password:

/dev/cdrom:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


> **cptnapalm said:**
> hdparm can't change setting on scsi style devices, which includes SATA, as far as I know.  While there is a sdparm, it does not have the functionality of hdparm.

Since the OS is listing it as scd0, that means that SATA is enbabled in the kernel.  I wonder if the problem is that the device itself is IDE, just with a SATA interface... that would explain why many people have this problem.

While a laptop, there is this guide which may be of use: [http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_cdrw_dvdrw_multi_burner](http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_cdrw_dvdrw_multi_burner)

I'm at work, so I'll get back if I can.

Well, it's an external drive attached via USB, so I don't know how to tell if it's a SATA or an IDE device. I'd assume IDE since non-HDDs generally seem to be an IDE interface still, but that's not really a guarantee...

But I don't really see the correlation. The interface is USB, so why does it matter if it's IDE or SATA? I also have 2 external hard drives, 1 320GB SATA drive in a SATA > USB enclosure, and 1 160GB IDE drive in an IDE > USB enclosure. If it was a SATA interface problem then shouldn't my 320GB SATA/USB drive run slowly (it doesn't)?

This seems fishy... This Lite On external CD burner is not an uncommon drive (the most popular external on Newegg actually), so I don't think it's especially peculiar. Does everyone else have slow burns from their external drives too?

---

### Post by sprocket87 on 2006-07-13
> **cptnapalm said:**
> actually, the output of "sudo hdparm -tT /dev/scd0" might be handy as well; I think having a disc in the drive might be required.

$ sudo hdparm -tT /dev/scd0

/dev/scd0:
 Timing cached reads:   2436 MB in  2.00 seconds = 1217.92 MB/sec
 Timing buffered disk reads:   10 MB in  3.17 seconds =   3.15 MB/sec

---

### Post by sprocket87 on 2006-07-13
Update: It's now burning at 16-18x in several apps (so far I've tried Serpentine, bonfire, and k3b - no gnomebaker yet). I don't know what it was - I've restarted since my last attempts, but I haven't really changed anything else. I ran the hdparm -d1 /dev/scd0, but as the snippet above shows that shouldn't have worked.

Well, 16-18x is more liveable, but definitely not the 48x it should be (or that I get in Windows :confused: )

PS - why does k3b have to be run as sudo to see the /dev/scd0 drive? The other apps don't...

---


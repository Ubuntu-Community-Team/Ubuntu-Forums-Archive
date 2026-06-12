---
title: "Enabling DMA problem"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Aber_Adrian on 2005-11-21
I've searched here ans elsewhere for my answer, but none of the ideas work.

I have just installed Breezy on my system following a hard disc failure (previously a Mandrake 9.1 user). I now have a SATA hard drive, an IDE CD-RW on primary master and an IDE DVD on primary slave.

Ubuntu in its wisdom has decided to make the CD /dev/scd0 and the dvd /dev/scd1 (using scsi-ide). Therefore, an hdparm -d1 won't work:

hdparm -d1 /dev/scd1

/dev/scd1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

I believe other threads suggested there may also be another route to the device such as /dev/hdb. No such luck; I only have one dev beginning with h and it's not an hd.

The same computer with the old hard drive running Mandrake played DVDs beautifully, no problem. This just misses too many frames to be acceptable. With hdparm -t /dev/scd1 giving:

/dev/scd1:
 Timing buffered disk reads:    8 MB in  3.23 seconds =   2.47 MB/sec

that's not surprising.

nvidia card is configured with nvidia driver, so that's OK. But I'm suspicious of: cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1

That's not right either, is it?

All I can think of is recompiling the kernel; is there no easier way? And if I do need to recompile the kernel, what modules do I need to include? And what should I leave out?

Many thanks for any answers.

Adrian

---

### Post by 23meg on 2005-11-21
It shouldn't make the IDE CD-RW a SCSI device in the first place; there's something wrong in *there.* Are you sure you haven't explicitly enabled SCSI emulation for that drive beforehand? In any case you won't be able to modify the settings of a SCSI / SATA device with hdparm.

---

### Post by Aber_Adrian on 2005-11-21
[QUOTE=23meg]It shouldn't make the IDE CD-RW a SCSI device in the first place; there's something wrong in *there.* Are you sure you haven't explicitly enabled SCSI emulation for that drive beforehand? In any case you won't be able to modify the settings of a SCSI / SATA device with hdparm.[/QUOTE]

No, I thought it was strange.

Installing in expert mode failed twice, both at the bootloader installation stage (both grub and lilo attempted) so I ended up just doing a basic standard install, so not a lot of scope for *me* doing anything wrong there.

I suspect it has to do with a SATA hard drive confusing something somewhere along the line, but I don't know.

Time to recompile a kernel?

Adrian
****

---

### Post by 23meg on 2005-11-21
I don't think you have to recompile the kernel; what you have to do is explicitly tell Ubuntu that your CD-RW is an IDE drive and not a SATA but honestly I don't know how you have to do that. Did you try different master / slave configurations and / or plugging the IDE CD drives into another IDE bay and in different orders?

---

### Post by Aber_Adrian on 2005-11-21
[QUOTE=23meg]I don't think you have to recompile the kernel; what you have to do is explicitly tell Ubuntu that your CD-RW is an IDE drive and not a SATA but honestly I don't know how you have to do that. Did you try different master / slave configurations and / or plugging the IDE CD drives into another IDE bay and in different orders?[/QUOTE]

No I haven't tried that. I did consider it but thought it wouldn't make any difference. However, I'll give it a go tomorrow and report back.

In the meantime, if anyone does know how to tell Ubuntu that they're IDE not SCSI drives, please reply!

Adrian

---

### Post by Aber_Adrian on 2005-11-22
[QUOTE=23meg]I don't think you have to recompile the kernel; what you have to do is explicitly tell Ubuntu that your CD-RW is an IDE drive and not a SATA but honestly I don't know how you have to do that. Did you try different master / slave configurations and / or plugging the IDE CD drives into another IDE bay and in different orders?[/QUOTE]

OK I have now tried plugging the IDE cable into the secondary bay. Bios correctly detects as secondary, and puts the SATA hard drive as primary master. But the CD & DVD drives are still put on /dev/scd0 and /dev/scd, and there's still no /dev/hd*. hdparm therefore still can't set DMA; it still thinks they're SCSI devices.

Where to next? If no-one knows how I can tell Ubuntu that they're IDE drives, I guess it's a new kernel :mad:. Anyone?

Adrian

---

### Post by 23meg on 2005-11-22
What kernel are you using at the moment?

---

### Post by Aber_Adrian on 2005-11-22
[QUOTE=23meg]What kernel are you using at the moment?[/QUOTE]

It's the one that came with Breezy - 2.6.12.9-386.

I've actually just set a 2.6.14.2 compiling. I'll see if I can get it installed.

Adrian

---

### Post by 23meg on 2005-11-22
What's your processor? Did you try the 686 kernel?

---

### Post by Aber_Adrian on 2005-11-22
[QUOTE=23meg]What's your processor? Did you try the 686 kernel?[/QUOTE]

It's a Celeron 2600. No I didn't try the 686 kernel - I am just using what the installation procedure installed.

Adrian

---

### Post by 23meg on 2005-11-22
Try it; you should be using it instead of the 386 one anyway and it may -somehow, magically- fix things for you as well.

---

### Post by Aber_Adrian on 2005-11-22
Well I took the plunge and compiled a new kernel. Obviously I missed something, though I can't figure out what, because the new kernel (2.6.14-2) won't even see my CD or DVD drives. I disabled SCSI-IDE, because I thought that may have been the problem on the original kernel, as well as there being some message in the config menu that this isn't necessary now anyway. So still no luck.:( 

I used the Processor family (Pentium-4/Celeron(P4-based)/Pentium-4 M/Xeon) option, which I assume is what you meant.

I'd post the .config file here except I don't suppose it would be very welcome!

Do I give up? 

Adrian

---

### Post by jpkotta on 2005-12-18
I had the DMA with SATA problem too.  Apparently, libata and ide_generic modules do not get along.  I did a ```
sudo rmmod ide_generic
``` and DMA worked, with quality DVD playback.  That command may mess up your system, but if it does, it won't be permanent (just reboot).  

So here's the weird part.  I tried to disable the ide_generic module from loading at boot by commenting out all references to it in /etc/modprobe.d/aliases.  That didn't stop it from loading, but DMA still works, so I assume that it gets loaded in such a way so that it plays nice with libata.

I got the idea from [here]("http://forums.gentoo.org/viewtopic-t-341337-highlight-d610+dma.html").

---


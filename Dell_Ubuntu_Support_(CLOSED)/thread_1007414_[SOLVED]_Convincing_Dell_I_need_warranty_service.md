---
title: "[SOLVED] Convincing Dell I need warranty service"
date: 2008-12-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by occams_beard on 2008-12-10
Hi,

I have a Dell Insprion 530 desktop that came with Vista pre-installed.  However, I dual boot with Ubuntu as my primary OS. 

I'm having issues which I believe are hardware related. What happens is that I'll boot up in the morning and about 2 minutes later, the computer will freeze for about 1 minute whilst the hard drive makes a kind of nasty repetitive seek noise.  Looking at the log after this happens suggests that the SATA link is reseting it's self.   Curiously, this only occurs after a cold boot when the computer has been off for a few hours.  Thus, my guess is that either the drive, mobo, or PSU is flaking out as the machine warms up. Not sure which one.

The computer is still under warranty for a few more months... BUT, This problem doesn't occur under Vista, so how do I convince Dell that the hardware is faulty?  Dealing with their tech support is an, uhh, interesting experience... and I'm sure they will not be willing to read the script for my problem, which only manifests itself under Linux. 

Any advice or tips on dealing with them?

---

### Post by gbrainin on 2008-12-10
Have you tried (if you have not deleted it already) using the diagnostic partition that came with the computer?  I would try running the hardware test through that, see if it comes up with an error.

---

### Post by occams_beard on 2008-12-10
I ran it a couple times between an installation of Ubuntu and Fedora 10 when grub wasn't installed and it checked out ok.

When grub is installed I can't get to it. Selecting the diagnostic partition in the BIOS boot menu just dumps me at the grub menu.

Would be interesting to see what the dell diagnostics say when the machine is cold.  How can I get to the diagnostics with grub installed?

---

### Post by occams_beard on 2008-12-11
I figured out I can add the Dell utility partition to grub by adding:

title Dell diagnostics
rootnoverify (hd0,0)
chainloader +1
boot

..at the end of /boot/grub/menu.lst.

Anyway... I ran the extended test and everything passes. Ugghh. This is frustrating because I'm 99% certain it's a hardware problem. It's either the hard drive (doubtful), mobo, or PSU. I have no idea which.

I wonder how I should proceed with Dell?

---

### Post by gpsmikey on 2008-12-11
You might also consider downloading the disk test utility from the drive manufacturer (they usually have one) and run that.  See what it reports about the drive (that is what the drive manufacturers usually want to see anyway for warranty returns).

mikey

---

### Post by occams_beard on 2008-12-11
I've tried that as well. It's a Western Digital drive so I ran their diagnostic utility under windows. In addition to that, I've run smartmontools, badblocks, Drive Fitness test, HD tune, chkdsk, etc.  The drive always passes any diagnostic I throw at it.

The weird thing about this is that it only happens when the computer is physically cold and has been off for at least 6 hours. Like in the morning when I first boot up it will usually do it, but then it'll be fine for the rest of the day. So I can only conclude it's a hardware problem of some kind.

According to the the log, it looks like the SATA link is dropping out when this occurs. The drive will totally spin down and then spin up again.

```

Dec  8 20:13:18 pandora kernel: [  114.724095] ata1: hard resetting link
Dec  8 20:13:23 pandora kernel: [  120.240030] ata1: link is slow to respond, please be patient (ready=0)
Dec  8 20:13:28 pandora kernel: [  124.786752] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  8 20:13:28 pandora kernel: [  124.786767] ata1: link online but device misclassified, retrying
Dec  8 20:13:28 pandora kernel: [  124.786773] ata1: hard resetting link
Dec  8 20:13:33 pandora kernel: [  130.300024] ata1: link is slow to respond, please be patient (ready=0)
Dec  8 20:13:38 pandora kernel: [  134.846759] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  8 20:13:38 pandora kernel: [  134.846775] ata1: link online but device misclassified, retrying
Dec  8 20:13:38 pandora kernel: [  134.846780] ata1: hard resetting link
Dec  8 20:13:44 pandora kernel: [  140.360031] ata1: link is slow to respond, please be patient (ready=0)
Dec  8 20:14:13 pandora kernel: [  169.882771] ata1: SATA link down (SStatus 21 SControl 300)
Dec  8 20:14:18 pandora kernel: [  174.880050] ata1: hard resetting link
Dec  8 20:14:20 pandora kernel: [  176.364082] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  8 20:14:20 pandora kernel: [  176.392722] ata1.00: configured for UDMA/133
Dec  8 20:14:20 pandora kernel: [  176.392736] ata1: EH complete
Dec  8 20:14:20 pandora kernel: [  176.421707] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Dec  8 20:14:20 pandora kernel: [  176.429618] sd 0:0:0:0: [sda] Write Protect is off
Dec  8 20:14:20 pandora kernel: [  176.439994] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by notwen on 2008-12-11
Have you tried swapping out the drive temporarily w/ another SATA drive?  Just an idea.

---

### Post by occams_beard on 2008-12-11
Haven't tried that. I don't have a spare SATA drive, or know anyone I can borrow one from.  Funny thing about hard drives... no one ever wants to lend them out :)

---

### Post by notwen on 2008-12-11
> **occams_beard said:**
> Haven't tried that. I don't have a spare SATA drive, or know anyone I can borrow one from.  Funny thing about hard drives... no one ever wants to lend them out :)

Hah, know the feeling. lol

---

### Post by unutbu on 2008-12-11
Googling "link is slow to respond" turned up this:

[http://thread.gmane.org/gmane.linux.ide/31317/focus=31349](http://thread.gmane.org/gmane.linux.ide/31317/focus=31349)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297058](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297058)

It appears to be a linux kernel (libata) bug.

For the record, would you please post the output of 
```

sudo lshw -C disk
```

so we might know the exact make and model of your hard drive?

So the good news is, there might not be anything wrong with your hardware.
The bad news is that your hardware might not be Ubuntu-compatible at the present time.

You might want to try a different version of Ubuntu. These problems sometimes actually appear in a newer version but not in an older version. Or, you might want to try a different Linux distro. 

Alternatively, if you could purchase a second hard drive, say a USB external drive, then you could install Ubuntu there. If you buy the drive from a local store like Best Buy, you can try it out and return it if it turns out to be incompatible with Ubuntu.

---

### Post by occams_beard on 2008-12-12
Hmm, well I thought it could possibly be a bug but I'm not quite sure because it only seems to happen when the machine is cold.  Not sure how that could make a difference to software. Also, my log is slightly different from those links.  Specifically the part about:

"ata1: link online but device misclassified, retrying"

Googling that doesn't turn up much at all. And also sometimes when it happens it'll log exception details like...

```

Dec  1 11:22:28 pandora kernel: [  735.000049] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 11:22:28 pandora kernel: [  735.000061] ata1.00: cmd 35/00:08:8d:94:c9/00:00:14:00:00/e0 tag 0 dma 4096 out
Dec  1 11:22:28 pandora kernel: [  735.000063]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  1 11:22:28 pandora kernel: [  735.000067] ata1.00: status: { DRDY }
Dec  1 11:22:28 pandora kernel: [  735.000075] ata1: hard resetting link
Dec  1 11:22:33 pandora kernel: [  740.512011] ata1: link is slow to respond, please be patient (ready=0)
Dec  1 11:22:38 pandora kernel: [  745.048015] ata1: SRST failed (errno=-16)
Dec  1 11:22:38 pandora kernel: [  745.058743] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  1 11:22:38 pandora kernel: [  745.058753] ata1: link online but device misclassified, retrying
Dec  1 11:22:38 pandora kernel: [  745.058759] ata1: hard resetting link
...

```

and other times when it happens it will omit the Emask stuff all together. Very strange.

From what I understand (I may be wrong) the log seems to indicate that the controller is loosing communication with the drive.  I would love for it to just be a bug though. Ugh, it's so hard to diagnose this sort of thing :mad:

I should also mention that this problem seemed slightly worse under Hardy. It would occur when booting. Under Intrepid, it occurs about 30 - 60secs after I get to my desktop. That might be because Intrepid seems to boot a little faster tho... It also occurs with Fedora 10.

The output from sudo lshw -C disk gives:

```

  *-disk                  
       description: ATA Disk
       product: WDC WD5000AAKS-7
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 12.0
       serial: WD-WCAS87066186
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=08000000
  *-cdrom
       description: DVD writer
       product: DVD+-RW GSA-H73N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: B103
       serial: [HL-DT-STDVD+-RW GSA-H73NB10307/06/27 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc


```

---

### Post by occams_beard on 2008-12-13
Just an update... This problem is now happening under Windows, so it's definitely a hardware problem... bleh.  

I absolutely dread the thought of having to deal with Dell.  Hopefully it's only the hard drive and they can ship out a new one and let me install it myself.

---

### Post by jdeal on 2008-12-13
I have been following this thread with interest.  I am not sure if I have the similar problem.  I have a Dell Vostro 200 desktop dual boot with Vista and Ubuntu 8.04.1 (64-bit) new in August 2008.  Installed 8.04.1 and worked great for months although not used often.  The I ran updates with new kernel (-21).  Then started not booting all the time taking several tries.  I then tried booting off the old kernel (-19) and same problem.  Got to a point it would not boot at all.  Doing <cntl><alt><F1> to get messages and get: "ata01:00 Revalidation failed errno=-5".  These would continue moving to ata02 etc.

I tried booting off the original 8.04.1 CD I used to install the OS and get a initramfs prompt.  I then tried a 8.04.01 (32-bit) CD that I used for many installs and the same thing.  I tried a Fedora F10 (alpla) Live CD and it booted fine.  It also boots Vista from the hard disk every time without fail.

Looking at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635) that also seems to have this problem.  I tried when in grub replacing the quite splash with irqpoll all_generic_ide but it did not make any difference on either the -19 or -21 kernels.  This same OS from the same CD runs fine on my Dell 1525 laptop.  I can not change my menu.lst as stated in the referenced report since I can't book my system in Ubuntu at all.

Does anyone know if this is fixed in 8.10?  The development project that I am working on will not work with 8.10 but it is better than being stuck with Vista.  This system was purchased to do this project.  This has been a very frustrating and time-consuming process.

Thanks.

---

### Post by occams_beard on 2008-12-13
When I was running Hardy, I had a problem where it would refuse to boot up at all. I was able to boot the live CD and it turned out that my file system had become corrupt.  Luckily I was able to repair it from gparted on the Live cd.

Probably not the same problem you're experencing, but might be worth a try nevertheless. If you can't boot the Ubuntu CD, you might want to try burning a gparted cd and trying that [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by notwen on 2008-12-14
> **occams_beard said:**
> When I was running Hardy, I had a problem where it would refuse to boot up at all. I was able to boot the live CD and it turned out that my file system had become corrupt.  Luckily I was able to repair it from gparted on the Live cd.

Probably not the same problem you're experencing, but might be worth a try nevertheless. If you can't boot the Ubuntu CD, you might want to try burning a gparted cd and trying that [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

In your previous post you said it began occurring for Vista too, just curious if both file systems ended up being corrupt?

---

### Post by occams_beard on 2008-12-14
No, Vista's NTFS partition was fine. Just my / ext3 partition bit the dust.

---

### Post by notwen on 2008-12-14
> **occams_beard said:**
> Just an update... This problem is now happening under Windows, so it's definitely a hardware problem... bleh.  

I absolutely dread the thought of having to deal with Dell.  Hopefully it's only the hard drive and they can ship out a new one and let me install it myself.

So Vista is no longer having the problems?  Was that just a one-time coincidental occurrence maybe?  Weird.

Regardless, looks like you can mark this thread solved.  =]

---

### Post by occams_beard on 2008-12-15
The corrupted ext3 partition was a one time occurrence possibly. It hasn't done it since.  However, I still have the problem with the drive freezing up like I originally described.

I contacted Dell and they're sending out a new drive. Hopefully that will fix it once and for all.

---


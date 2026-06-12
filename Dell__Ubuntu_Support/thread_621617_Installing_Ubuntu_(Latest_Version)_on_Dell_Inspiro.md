---
title: "Installing Ubuntu (Latest Version) on Dell Inspiron 1720"
date: 2007-11-23
forum: Dell  Ubuntu Support
---

### Post by killmyself on 2007-11-23
Hi all. First of all I'm new in this thing of Linux and its distributions. I didn't know which one to choose but I chosed Ubuntu because it was number 1 in Distro-Watch. I have recently bought a Dell Inspiron 1720 with the following characteristics:

Intel Core 2 Duo T7700, 2.4GHz, 800Mhz, 4M L2 Cache
2GB, DDR2, 667MHz 2 Dimm for Inspiron 1720
256MB NVIDIA GeForce Go 8600
120G 5400RPM SATA hard drive 5400RPM
Intel 3945 WLAN (802.11a/g) Mini Card
Dell Wirless 355 Bluetooth Mod
Basic Black Matte LCD back color w/ 2.0M pixel Camera Insp 1720

Second of all, I have to say that I've tried every version of many distributions and none worked. Ubuntu 7.04 doesn't work, NUBUNTU neither, Ubuntu (latest) neither, etc. Every version crashed when I ran the LiveCD... Ubuntu's error was something with /etc/rc.local and it stopped there. I would like some help to install Ubuntu as a Virtual Machine and as another partition in my hard drive. Would it be possible to use everything that I have in Windows Vista? What other distribution shall I use?


PS: For all Inspiron 1720 users there's no driver for some Bluetooth Peripheral Device

---

### Post by derby007 on 2007-11-24
Yeah, its a graphics problem, I had it too. Try the Alternate CD version (Text based) installer. 

Alternate download: ubuntu-7.10-alternate-i386.iso
Live (desktop AMD) : ubuntu-7.10-desktop-amd64.iso

Note: i386 means for the Intel based processors.
AMD64 is for AMD 64bit processors, although i386 would work on an AMD PC.

---

### Post by cmccauley on 2007-11-24
Hi,

I also have an Inspiron 1720 and was very pleased when the Live CD picked up my wireless network connection and set the graphics resolution correctly. The only real problem was the audio which needed tweaking. 

As a long term Linux user, I've found that many problems with installation are related to  either an incomplete download or a fault on the installation medium. 

Chris

---

### Post by killmyself on 2007-11-24
Thank you for your support :P. 

Well, I'm downloading the alternate CD for 64 bits-CPU and the alternate CD for i386. So which one should I install? I've also got a question. When I was installing Vista there was a problem with the SATA hard drive. I needed to specify a driver from Dell's Drivers&Utilities CD so I could go through the installation. What do I have to do when I'm installing Ubuntu? Should I specify a driver? I can't change the BIOS otherwise I'm losing my other OS

---

### Post by Jeff_From_VA on 2007-11-25
> **killmyself said:**
> Thank you for your support :P. 

Well, I'm downloading the alternate CD for 64 bits-CPU and the alternate CD for i386. So which one should I install? I've also got a question. When I was installing Vista there was a problem with the SATA hard drive. I needed to specify a driver from Dell's Drivers&Utilities CD so I could go through the installation. What do I have to do when I'm installing Ubuntu? Should I specify a driver? I can't change the BIOS otherwise I'm losing my other OS

I do not have this particular laptop yet - I found this thread when looking for a laptop for my wife. I picked out that same dell, and am now looking  to make sure it was linux compatible.   

But as a general rule - you don't have to do anything for the sata drive.  Ubuntu should find it on it's own.  At least that has been my experience on every other Sata/linux install.   

As to which to install - your core 2 duo can run either i386 (32 bit) or the amd64 (64 bit)  -- I run 64 bit on the machine I am typing this to you on, and I love dit.  But, it is a pain to get some things working right as they were designed for 32 bit.  If you want hassle free go 32 bit, if you are willing to tinkler to get some things up and want the small performance boost, go 64 bit.

---

### Post by RockHaxor on 2007-12-17
I have the same laptop as you and tried to install gutsy. I finally got it installed with many problems and tried to reinstall vista but the hard drive isn't found.Very strange. Don't know what do this laptop is brand new.

---

### Post by HeavyAl on 2007-12-18
> **RockHaxor said:**
> I have the same laptop as you and tried to install gutsy. I finally got it installed with many problems and tried to reinstall vista but the hard drive isn't found.Very strange. Don't know what do this laptop is brand new.

Hey there. I had that same problem. There are a couple ways you can get around it. 

If you have a live recovery cd like 'Bart PE' then you can boot that and use fdisk to first remove the old partitions and then use fdisk /mbr to write a boot sector that Vista will recognize. 

If you don't have a recovery cd of any kind then a really 'redneck' way of fixing this problem is to try to install Windows XP or 2000 - both of those will recognize the drive even though Vista won't .. you don't have to do the full install of the OS if your intention is to go back to Vista - just go through the partitioning parts of the operation so that the partitions and boot sectors are written (probably have to wait as far as the first reboot on XP or 2K). 

Seriously, it's a weird problem for Vista to have, but chalk that up to the great list of oddities that you'll be choosing to deal with if you go with it. I've personally run Vista for several months so that when I run into customers who use it I won't be totally in the dark, but to be completely honest I personally think that Vista is a step backwards.

Anyhow, hope that helps.

---

### Post by RockHaxor on 2007-12-19
Hmmm, I tried to install xp and am having the same problem. I had found on the net that it may be a sata driver problem not included on the installation disk and that the drivers should be installed during setup when it asks if you need to install any third party scsi or sata drivers press F6. Problem is it asks for the drivers on drive a: and I don't have a floppy drive on my laptop. Ugg, what the heck

---


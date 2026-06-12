---
title: "Is Ubuntu right for me?"
date: 2011-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GpD79 on 2011-09-26
Good Evening All!
 
I'm very new to the idea of Linux. My mac recently died so I bought a Dell XPS 15 laptop. I would of liked to buy another mac, but they're way too expensive. I've heard some really great things about Linux and Ubuntu that I thought I should look into it. To make a long story short, I bought a Dell and I've been thinking of installing Ubuntu, but how do I know that all of the features will work?
 
Here is a description of the computer:

1 2nd generation Intel Core i7-2630QM processor 2.00 GHz with Turbo Boost 2.0 up to 2.90 GHz
1 6GB,DDR3,2 DIMM
1 Backlit Internal Keyboard - English
1 15.6HD TLF WLED LCD L50xX
1 NVIDIA GeForce GT 525M 1GB graphics with Optimus
1 750GB 7200 RPM SATA Hard Drive
1 Genuine Windows 7 Home Premium 64 bit Service Pack 1, English, No Media
1 Tray Load Blu-ray Triple Writer (reads and writes CDs, DVDs, BDs)
1 JBL 2.1 Speakers with Waves Maxx Audio 3
1 Intel Centrino Wireless-N 1030 and Bluetooth 3.0
1 90 WHr 9-cell Lithium Ion Primary Battery
1 Microsoft Office 2010 Home and Student, English
1 2.0MP HD webcam with single digital mic (H.264)
1 Mini DisplayPort (1),
2 USB 3.0
1 USB 2.0 (eSATA/powershare combo)
1 Integrated network connector 10/100/1000 LAN (RJ45)
1 HDMI 1.4
1 Audio jacks: headphone (2 total) with SPID/F support (1), 1 Mic-in
1 9-in-1 media card reader Supporting SD, SDIO, SDXC, SDHC, MS, MS Pro, MMC, MSXC, xD
 
 
My concern is that not everything will work; such as the bluetooth, blu-ray player, webcam, etc. I have the computer sitting here in the box and I don't know if my computer is compatible with Ubuntu. Also, if I do decide to install it, should I use the 32 bit or the 64 bit? My computer right now is 64 bit, but on the website it says it recommends 32 bit. 
 
Your thoughts and insight will be very appreciated!
 
Thanks,
Graz

---

### Post by lykwydchykyn on 2011-09-26
Generally Dells work very well with Ubuntu or other Linux distributions, though I've had trouble with suspend & resume and other power-management features with some releases.

Best way to find out is to download the CD and boot to it.  You can just try Ubuntu without actually installing it by running from the CD.

As for 64 bit vs 32 bit -- there's not a big difference any more.  In my experience 64 bit is pretty mature and most things I've needed have worked just fine (the things that haven't are fairly esoteric).

With 6 GB of RAM, going 64bit is probably worthwhile.

---

### Post by MG&amp;TL on 2011-09-26
The webcam seems to work pretty good on everything I've tried. Same with the bluetooth.
Wireless can be more dodgy, but burn a cd/usb and try it out. If you want to experience the speed of linux/ubuntu, you're probably better off with a USB.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by F.G. on 2011-09-26
yeah, so, give it a go. see if you like it. generally, as linux goes,  ubuntu is pretty compatible with alot of hardware so i hope you'll be pleasantly surprised.
either way you can run it with a live cd/dvd/usb or do a dual boot install with Windows7 and keep the Windows. and try it before you commit.

ps also if you want to OSX will run with the intel core processor you've got, so you can still run the Mac OS if you really liked it.

also 32 bit is recommended because it will work on both 32 and 64 bit architecture (basically anything). If you know you've got 64 bit hardware, go with that (they're both free, and if you try 64 bit on a 32 bit machine it will simply not work, you wont break anything).

---

### Post by ninjaaron on 2011-09-27
You will have to install the Nvidia drivers with that machine.  It's done with a couple of clicks, but you will get funny video performance until you do it.

It's not a major issue.  I haven't heard anyone talk about problems with any of the other hardware on that machine.  If there are issues, they are probably very small and can be fixed with a google search and a text editor (Linux loves human-readable, plain-text config files.  I thought this was funny and backward at first, but now I love it.  Everything is there in black and white).

---

### Post by BBQdave on 2011-09-27
I too come from a Mac world.  I started out with OS9 and worked with macs thru 10.4.11 (Tiger).  Along side my macs I always had a Linux machine going.

I now work only on Linux machines (Debian6 on an old dell inspiron), and my last remaining mac is an eMac that I use as a file and print server.

Give Ubuntu a fair chance and stick with it, I think you'll find GNU/Linux a rewarding and liberating experience:D

---

### Post by GpD79 on 2011-09-28
Thanks guys for all of the great feedback.  I think I'm going to take the plunge.  I was on the phone with Dell Support yesterday and lucked out because the guy on the phone was a big Linux user.  He gave me some good advice.  First he stated that instead of doing a clean install, I should install Ubuntu alongside Windows 7.  He said that if I install only Ubuntu, I will no longer be able to get support from Dell since they're not trained on it.  He said it would be a good failsafe because in case hardware went bad, they would be able to check it via Windows 7.  Makes sense.  
 
He then instructed me to install 10.04 instead of 11.04.  He stated that 11.04 isn't supported yet because it is still in beta.  That confused me because it doesn't say it's a beta version.  He was very adamant about that point.  Is that true?  Should I install 10.04 LTS instead of 11.04?  Also, do you think installing Ubuntu alongside Windows 7 is a good idea?
 
Your advice is GREATLY appreciated.  Thanks!

---

### Post by GpD79 on 2011-09-28
> **ninjaaron said:**
> You will have to install the Nvidia drivers with that machine. It's done with a couple of clicks, but you will get funny video performance until you do it.
 
It's not a major issue. I haven't heard anyone talk about problems with any of the other hardware on that machine. If there are issues, they are probably very small and can be fixed with a google search and a text editor (Linux loves human-readable, plain-text config files. I thought this was funny and backward at first, but now I love it. Everything is there in black and white).
 
Is it difficult to install the Nvidia drivers?  How would I go about doing that?  
 
THANKS!

---

### Post by MG&amp;TL on 2011-09-29
He is out of date about 11.04, it's 11.10 you want to watch.

For the drivers, open system>>administration>>hardware (additional?) drivers, and choose the reccommended one. Reboot. Done. :D

windows alongside ubuntu is fine. Just be careful. Whatever you do, however, do NOT use system recovery disks unless you like booting to a grub command-line.

---

### Post by vasa1 on 2011-09-29
> **GpD79 said:**
> ... 
He then instructed me to install 10.04 instead of 11.04.  He stated that 11.04 isn't supported yet because it is still in beta.  That confused me because it doesn't say it's a beta version.  He was very adamant about that point.  Is that true?  Should I install 10.04 LTS instead of 11.04?  Also, do you think installing Ubuntu alongside Windows 7 is a good idea?
 
Your advice is GREATLY appreciated.  Thanks!

A couple of newbie thoughts ... IMO, Dell guy isn't very wrong. The LTS releases are regarded as stable and the others aren't even though they aren't tagged as such.

The other thing which I read somewhere, is that Windows Updates has the potential to interfere with loading Ubuntu on a dual boot PC. So you may want to ask for advice on that aspect as well.

---

### Post by ninjaaron on 2011-09-29
> **vasa1 said:**
> A couple of newbie thoughts ... IMO, Dell guy isn't very wrong. The LTS releases are regarded as stable and the others aren't even though they aren't tagged as such.  I disagree.  The LTS is preferable for server and enterprize deployment where you are trying to coordinate a lot of machines and need to know all of the system elements inside and out.  The other releases should be fine for the average desktop user.  It's true that each new release has bugs when it comes out, but most of these get fixed within the first month, and the LTS is no exception in this regard,

> The other thing which I read somewhere, is that Windows Updates has the potential to interfere with loading Ubuntu on a dual boot PC. So you may want to ask for advice on that aspect as well.
This will probably be more an issue in Windows 8.  I haven't heard about any problems dual booting with XP, Vista, or Win7.

---

### Post by cabotcat on 2011-10-01
Take the plunge. I also come from an Apple background. Currently running a Latitude E6410 that has been wiped of everything but Ubuntu 11.04. Amazing machine and great OS. Nothing I cannot do with this setup. People on this board have been and will continue to be my mentor but make no mistake, I am all in.

The upside? Amazing speed stability and cost ain't bad. Won't catch me going back. ):P Windows!

---

### Post by Phateless on 2011-10-01
So here's a question. I've heard streaming doesn't work on Linux? Flash, like watching tv at fox.com, etc.

Can anyone speak to that?

---

### Post by GpD79 on 2011-10-14
Thanks guys for all of your help!

---


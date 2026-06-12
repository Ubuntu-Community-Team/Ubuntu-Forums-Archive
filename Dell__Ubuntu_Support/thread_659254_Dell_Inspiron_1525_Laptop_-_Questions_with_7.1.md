---
title: "Dell Inspiron 1525 Laptop - Questions with 7.1"
date: 2008-01-05
forum: Dell  Ubuntu Support
---

### Post by dhedrick on 2008-01-05
First, thanks in advance for your help - I'm not a complete novice with computers, but am completely new to Linux, and am excited about making the conversion, but a little nervous too since this laptop will be both a business and personal machine for me...

I was planning to either purchase a 1520 and dual boot with WXP, or purchase a 1420n already installed with Ubuntu 7.10, but neither of those is going to work.  The 1420n does not have enough of the options that I am interested in available for purchase (larger HDD, webcam, etc.), so I had planned on building a 1520 with WXP.  It appears that as of 2008, Dell is no longer making the XP version an option, and has also changed some of the available options with the 1525 (no NIVDA option is my biggest concern)

Now I'm looking at building a Inspiron 1525 laptop with the specs below - it will come factory installed with Vista, which I don't want at all, so I'm currently planning on using the Dell 7.10 ISO to wipe out Vista and install Gutsy instead.  My plan is to have 3-4 HDD partitions because I know that I want a personal drive separate so that when I upgrade in the future I don't have to worry about backing up all of my personal & business files (I was thinking root, swap, personal, & work - will this work?)  Can anyone give me some insight into what problems I'm likely to encounter with this transition so that I can make sure I'm prepared and get up & running asap - I don't want to be traveling and trying to sort out Ubuntu at the same time...

Intel Core 2 Duo T7250 (2.0GHz)
Glossy Widescreen 15.4" display (1280x800)
Intel Graphics Media Accelerator X3100
3GB RAM
250GB SATA HDD (5400RPM)
8x DVDRW
Intel Next -Gen Wireless -N Mini-card
Dell Wireless 355 Bluetooth Internal (2.0 + Enhanced Data Rate)
2.0M Pixel Webcam
9 Cell Battery
High Definition Audio 2.0
Integrated 10/100 Network Card
Integrated Modem

That's it...

My main questions that I'm unsure of the answer to are about the X3100 and the wireless -N, but I would really like to get any/all thoughts on how much trouble this is going to give me "out of the box" once I install the Dell Gutsy ISO.

Finally, I'm also curious about the feasibility of setting up a VPN so that I can use Citrix through my Firefox browser to access my company network on the road (as I currently do with WXP)

I know that this is pretty darn close to a novel, but I really appreciate any/all input that I can get.  I've done a lot of research to try to prepare myself for this, and am really looking forward to making this transition - just a little scared as  well.

Thanks again!

---

### Post by NovaAesa on 2008-01-07
I'm thinking of getting a Dell Inspiron 1525 as well. Main thing I want to know (as does dhedrick) is how much trouble the Intel X3100 will give me.

---

### Post by mudguts on 2008-01-08
I think that there are threads / posts dedicated to installing 7.1 on a 1520.

I have a 1520 with 2HDD's that I swap between when bored.

one is dual boot Vista / 7.1  

Vista has one good thing going for it... you can resize a partition and install Ubuntu w/ swap file.   If you go that route, make sure that you have a always on, dedicated lan cable into your Ubuntu partition so you can 'get' the fixes.  i.e. wifi and sound 

the other HDD is a XP / ubuntu dual boot.

XP will have some SERIOUS issues recognizing a SATA drive so you may want to stick with Vista.

there is a LOT of help on these boards.   You can ween yourself off of windows eventually.  I swap between XP andUbuntu quite a bit for work.

re: the 3100.  I have the Nvidia 128MB graphics card.  I think that the 3100 is a on board video card isn't it?  with Vista, you'll want a dedicated card to help with the insane amount of processing that Vista chews through.

---

### Post by 2GooD on 2008-02-20
Has anyone tried ubuntu-dell-1525n-intelvideo-reinstall.iso from [http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/) yet?

I'm trying tonight and posting my experiences in the [Dell category of my blog](http://www.divideandconquer.se/category/dell/).

\David

[http://www.divideandconquer.se/](http://www.divideandconquer.se/)

---

### Post by bluefox83 on 2008-03-22
is there a way to get the graphics driver without downloading that iso? i already have everything else working, i just need to get the intel graphics card up to par. and i REALLY don't want to reinstall ubuntu over one freakin file!

---

### Post by notwen on 2008-03-23
> **NovaAesa said:**
> I'm thinking of getting a Dell Inspiron 1525 as well. Main thing I want to know (as does dhedrick) is how much trouble the Intel X3100 will give me.

I have a Inspiron 1420n w/ the Intel X3100 chipset.  I use Compiz-Fusion w/o any problems.  I resolved the video playback issues simply by changing my video output in VLC to 'no XV'.  Some people after still have issues after skipping the blacklist check.  Check this [thread]("http://ubuntuforums.org/showthread.php?t=582112") to skip the blacklist check and enable Compiz-Fusion on your X3100 equipped machine.  Feel free to post back if you run into any issue.

---

### Post by meustrus on 2008-03-23
I just want to note that Intel integrated graphics cards are not as crappy as most people think they are.  I ran Vista Ultimate for a few months on a Core Duo 1.6 processor with 1gb ram and an Intel GMA 945 graphics chip.  Aero was fluid and beautiful (though compiz/beryl is much prettier).  The X3100 is supposedly a better chip than the GMA 945, and I expect it to be as powerful as some midrange gaming computers of four to five years ago.  Comparing integrated graphics to the dedixcated graphics on gaming computers?  Yes, and they have MUCH better power management as well.

As for the wireless N card, my guess is that it's an Intel Wireless 4965 a/b/g/n card, as that is the new model that runs N.  The 802.11n standard is pretty new and you won't find it in many places, but nobody in the entire computer industry is going to seriously try and sell you a wireless card trhat isn't backwards compatible with at least 802.11b/g connections, which are what you will find in most home and business routers as well as hot spots around town.

And saying that XP will have serious issues with an SATA drive?  Please.  Vista has the same problems, it's just less forward with it.  If you don't load the SATA driver for your computer on the installation for XP when you boot the installation CD, it complains that there's no hard drive present.  If you try and install Vista without loading the driver, it will recognise the hard drive and install perfectly until the first reboot, at which point the system will load and the installation will freeze because for whatever reason Vista does not seem to load all of the drivers on the installation CD onto the hard drive operating system.

And by the way, install Windows on the system first.  The GRUB bootloader is a lot smarter than Windows and will not require any configuration to dual boot.  Unlike Windows, Ubuntu will detect other OS installations on your computer and automatically create GRUB entries for them.

---


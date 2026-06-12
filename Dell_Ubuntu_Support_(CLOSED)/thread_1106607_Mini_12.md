---
title: "Mini 12?"
date: 2009-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Roasted on 2009-03-25
I have a Mini 12 here. I couldn't install 8.10 on it for some reason, I assume a borked video driver. I booted to 8.10 on my external hard drive and it brought up a text user interface, with failed attempts being logged that the usplash couldn't be loaded.

Okay, fine. So I checked out dell.com and brought up the mini 12 and saw it comes with vista basic OR ubuntu 8.04.1. 

Okay, fine. So I popped in my 8.04.1 CD. Well, I couldn't see my wireless network. Grr...  whatever... so I was just going to install it anyway. I click on the installer, no hard drive found... wtf?

---

### Post by Talon2 on 2009-03-25
> **Roasted said:**
> I have a Mini 12 here. I couldn't install 8.10 on it for some reason.

What hardware is in the mini 12? Use this command in a terminal:

lspci

It is interesting that the Mini 12 comes with Ubuntu pre-loaded but yet it isn't listed on the main Dell Ubuntu page (US):

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

I found out it was available a while back while trying to buy a 1525 for a relative.  After 2 months I still did not have the system.  Dell really blew it with me.  I could not believe how incompetent Dell was with this sale.  I finally cancelled and went with System76.  System76 was like a breath of freash air.

---

### Post by Roasted on 2009-03-25
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 06)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 06)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 06)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 06)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 06)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 06)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 06)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 06)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 06)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 06)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
ubuntu@ubuntu:~$

---

### Post by Talon2 on 2009-03-26
I checked your lspci output vs. my Mini 9 output.

Your system has the new Poulsbo chipset which includes a new graphics chipset.  I can't say what the support level is for that chipset yet.  Dell pre-loaded systems come with modified versions of Ubuntu.  These modified distros include codecs, a dvd player and extra drivers.  

What you might do is try installing 9.04.  The beta is due today.  If you don't like beta's then the final version is due in about 3 weeks.

---

### Post by Roasted on 2009-03-26
So, wait, let me get this straight.

Dell made a laptop, known as the Mini 12. Yet the Mini 12 comes with 2 OS's. Yet the individual hardware on each Mini 12 is different due to the difference in the OS's. So Dell didn't build a computer that was Ubuntu friendly. Dell built a computer with Vista intentions and then ported some hardware in/out to make it Ubuntu happy, therefore leaving Vista Mini 12 owners with an incompatible Mini 12 for Ubuntu, right?

I hate Dell.

---

### Post by anjilslaire on 2009-03-26
> **Roasted said:**
> So, wait, let me get this straight.

Dell made a laptop, known as the Mini 12. Yet the Mini 12 comes with 2 OS's. **Yet the individual hardware on each Mini 12 is different due to the difference in the OS's.** So Dell didn't build a computer that was Ubuntu friendly. Dell built a computer with Vista intentions and then ported some hardware in/out to make it Ubuntu happy, therefore leaving Vista Mini 12 owners with an incompatible Mini 12 for Ubuntu, right?

I hate Dell.

Not quite. the MIni 12 has a different chipset than the Mini 9, and Dell simply has their own linux drivers that work with it at the moment.

As suggested, I'd try 9.04, due out very soon. There's a good chance the compatibility issues will be resolved, or shortly thereafter.

---

### Post by Roasted on 2009-03-26
> **anjilslaire said:**
> Not quite. the MIni 12 has a different chipset than the Mini 9, and Dell simply has their own linux drivers that work with it at the moment.

As suggested, I'd try 9.04, due out very soon. There's a good chance the compatibility issues will be resolved, or shortly thereafter.

I'm not comparing Mini 9 to Mini 12. I'm talking about the Mini 12 only.

From Dell's web site under "Tech Specs" of the Mini 12:

  Operating System	
Genuine Windows Vista®  Home Basic
Ubuntu Linux version 8.04.1

I have 8.04, 8.04.1, and 8.04.2, none of them work with flying colors. How is it my version of 8.04.1 are different than what Dell preloads? 

Did I mention I hate Dell?

---

### Post by anjilslaire on 2009-03-26
Ah, thats it.

The Dell version *is* different from the regular 8.04x images that you can get from Ubuntu, plain and simple.

---

### Post by Roasted on 2009-03-26
> **anjilslaire said:**
> Ah, thats it.

The Dell version *is* different from the regular 8.04x images that you can get from Ubuntu, plain and simple.



Is there any way to download the Dell version of 8.04? Or is that in some way shape or form proprietary to Dell?

---

### Post by starcannon on 2009-03-26
I don't know for sure if this will help, but some dell ubuntu iso's are available here:
[http://linux.dell.com/](http://linux.dell.com/)
Just follow the Ubuntu on Dell link at the top of the menu at the linux dell website; again though, I'm not sure and could not confirm whether it will have all the modules that a mini 12 requires.

GL

---

### Post by Roasted on 2009-03-26
I downloaded the recovery 8.04.1 ISO from the Dell Linux Wiki.

I created a USB startup disk with this particular ISO through my Ubuntu desktop and booted the laptop up. I got the splash screen, selected english, and had several options.

Dell Recovery (Intel Graphics)
Dell Recovery (AMD Graphics)
Dell Recovery (Nvidia Graphics)
Try Ubuntu Without Any Changes To Your Computer

I tried all options, even though I know this laptop has Intel graphics (courtesy of PC Wizard 2008 that I ran in the XP partition that's still on the laptop).

All of them leave me with a text based user interface.

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12_ Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) *insert flashing underscore here*

Yes, I've hit help, but I don't see boot, install, or anything that's relevant to what I want to do.

My goal here is to have a "LiveCD" through the USB flash drive, which I accomplished. However, I can't seem to get this damn Mini 12 to cooperate with Ubuntu.

Any ideas of what I can do before an expensive piece of equipment is ground to powder and flushed down the toilet?

---

### Post by sirebral on 2009-03-26
> **Roasted said:**
> 
Any ideas of what I can do before an expensive piece of equipment is ground to powder and flushed down the toilet?

If that is what you want to do I could use a new Mini 12.

You should find out your exact video card specs.  Intel what?

---

### Post by Roasted on 2009-03-27
Intel(R) Graphics Media Accelerator 500

---

### Post by kevinchannon on 2009-03-27
I don't know if it helps, but my Ubuntu Mini 12 (pre-installed by Dell) is set up to use a special Dell package repository at [http://del-mini.archive.canonical.com](http://del-mini.archive.canonical.com) There are some sections of the repository whose titles imply that they contain the respective bits that allow Ubuntu to work on their netbooks, such as:

[http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu) hardy-netbook-base
[http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu) hardy-dell-mini

The source code is also available for these repositories, does anyone think that it would be possible to get acquire the necessary drivers and such from this repository?

---

### Post by sirebral on 2009-03-27
> **Roasted said:**
> Intel(R) Graphics Media Accelerator 500

(o_O) WtF?  

O. So I have your problem right here:

> **GMA 500**

There is no sufficient driver support for the GMA 500. The driver wasn't developed in-house and will not work with kernels newer than 2.6.24. Newer distributions like Ubuntu 8.10 with a newer kernel will not work properly.

Found here: [http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)
Under the Linux section.

SO the problem is your video card is not supported by Linux.  I wonder what they are using in the Mini 12 with Ubuntu.  I have a GMA 950 (the 945GME) which is compatible.  Maybe when 9.04 comes out?

---

### Post by Roasted on 2009-03-27
sirebral - thank you for your time.

Dear Dell,
Please die.
-Roasted

---

### Post by namaku0 on 2009-03-27
How about using VESA driver while waiting for the real driver?

1) Edit xorg.conf
```
$sudo nano /etc/X11/xorg.conf
```
2) Find "Device" section
3) Change Driver's value to "vesa"
4) Save it by pressing CTRL+O and then exit (CTRL+X).

Example:
```

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    VendorName     "SuxVendor"
EndSection

```

---

### Post by Talon2 on 2009-03-28
This article contains some information that may be of help:

[http://www.phoronix.com/scan.php?page=news_item&px=NzE3NQ](http://www.phoronix.com/scan.php?page=news_item&px=NzE3NQ)

See the last paragraph.

---

### Post by Roasted on 2009-03-28
So basically the hardware in this laptop is rejected and no longer mainstream supported?

---

### Post by Talon2 on 2009-03-28
The conclusion I came away with after reading the Phononix articles was to avoid the Intel Poulsbo (GMA 500).

Intel has historically supported its products very well.  Maybe they will correct this situation.

Concerning Dell:  Dell seems determined to use some components that are not well supported.

---

### Post by Michael%S on 2009-05-02
I can't say how disappointed I am about all this. I really loved using the Mini 12 and thought the upgrade to LPIA Jaunty would be as easy as I heard it was on the Mini 9... Now I'm struggling to recover the Dell Hardy and will probably end up selling the thing or putting Windows on it. *shudder*

---

### Post by tyroeternal on 2009-05-02
The mini 12 is a major disaster because of the video drivers.  If you are okay with running Hardy (8.04 LTS) than the mini 12 does acceptably well.  The video drivers are half-useful with that version of ubuntu.

The thread [here]("http://ubuntuforums.org/showthread.php?t=1014534") has just pushed 475 posts and most likely the primary effort in getting the mini 12 working smoothly.  Combing over those posts as well as the wiki (found [here]("http://gma500.wiki-site.com/")) that has been started should get anyone one their way to running hardy with the latest (if you dare call them that) drivers available.

As was mentioned before, running jaunty leaves you with one option: vesa graphics.  Depending on your use of the system this may be all you need!  In any case it is worth looking at.

---


---
title: "Ubuntu and Windows 7 on Netbook"
date: 2010-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djab on 2010-01-28
I am looking into getting a netbook. I would love to run Ubuntu as my primary OS but I would need windows 7 as well. 
I was looking at a Dell netbook that comes with windows 7. I know there is a way to partition the hard drive and install a bootloader that will let me choose at startup. Does anyone know if the hardware etc will
support ubuntu? Also how would I do this? Should I run Ubuntu or Ubuntu netbook remix or does it really matter?
Here are the specs:

Intel®Atom®Processor Z530 (1.6GHz/533MHz FSB/512K Cache)
Genuine Windows® 7 Starter for Small Notebook PCs, 32bit, English
10.1" Widescreen Display (1024x600)
1GB* DDR2 SDRAM*
160GB, 2.5inch, 5400RPM SATA Hard Drive
Intel®Graphics Media Accelerator 500
No Mobile Broadband Selected
Wireless 802.11g (1397) Mini Card
56WHr Lithium-Ion Battery (6-cell)
Intel®Atom®Processor Z530 (1.6GHz/533MHz FSB/512K Cache)
1 Year Basic Mail-In Service Plan
Save $85 off this Dell Mini 10!

Thanks in advance!

---

### Post by rogue_0111 on 2010-01-28
Try installing Ubuntu in [virtualbox]("http://www.virtualbox.org/") or [wubi]("http://wubi-installer.org/") instead of dual boot. You can use Win7 and run Ubuntu in a virtual environment or visa versa. It's like training wheels for the noob.

Here's a video of virtualbox:

[http://tek-botics.webs.com/apps/vide...box-on-windows]("http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows")

--

---

### Post by texaswriter on 2010-01-28
Well netbook would kinda preclude VM. 

But, try a livecd to see if it supports your hardware. Specifically, most LiveCD's will connect to the internet if they support your ethernet adaptor / wireless adaptor. Also check any other hardware that is mission critical to using that netbook. 

I'd try a Jaunty LiveCD or the Karmic LiveCD. If you want to, try a Debian Lenny LiveCD as well.

---

### Post by djab on 2010-01-29
Ok thanks. I would like to use Ubuntu as my primary operating system. I dont think i would like to visualize my primary OS. I think a dual boot would be better. I know for a fact that the hardware would support Ubuntu because Dell has a model with exactly the same hardware that comes with Ubuntu. I think Dual Booting is my best bet. How would i do this? Should i run Ubuntu or the Ubuntu netbook remix or does it matter?

Thanks!
Andrew

---

### Post by snowpine on 2010-01-29
Not speaking from personal experience here, but I have heard lots of bad things about the Intel GMA500 graphics chip. More information here: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If you are a techie comfortable "tweaking" the system, it looks like there is a workaround. If you're new to Linux and want something that works "out of the box", I'd recommend an open-source-friendly graphics chipset like the Intel 945g. Personally I have been very happy with my Dell Mini 9, which requires no special graphics tweaks.

AFAIK, all the Dell netbooks have Broadcom wireless, which will require you to install a closed-source driver: [http://ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://ubuntuforums.org/showpost.php?p=8090292&postcount=1)

---


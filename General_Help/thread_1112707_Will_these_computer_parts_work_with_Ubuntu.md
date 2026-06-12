---
title: "Will these computer parts work with Ubuntu?"
date: 2009-03-31
forum: General Help
---

### Post by vodkashot on 2009-03-31
Hello, I am going to be getting a new computer, and I curious to know if these computer parts will be compatible with the newest Ubuntu realease. I intend to to play World of Wraft with Wine. And of course want the eye candy from compiz. Any suggestions / input would be greatly appreciated. 

Thank you!
-new user

> LG 20X DVD±R DVD Burner w/ SecurDisc Tech Black SATA Model GH20NS15 - OEM 

> Western Digital Caviar Green WD10EADS 1TB SATA 3.0Gb/s Hard Drive - OEM 

> Hanns&#8721;G HG-281DPB Black 27.5" 3ms Widescreen HDMI LCD Monitor - Retail 
is this screen's size / resolution supported with Ubuntu?
> SILVERSTONE ST1000 1000W ATX12V / EPS12V SLI Ready CrossFire Ready Modular Active PFC Power Supply - Retail 

> OCZ Gold 8GB (4 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Quad kit Desktop Memory Model OCZ2G8008GQ - Retail 
Can Ubuntu use all 8GM of ram?
> GIGABYTE GA-EP45-UD3L LGA 775 Intel P45 ATX Intel Motherboard - Retail 

> Intel Core 2 Quad Q9550 Yorkfield 2.83GHz LGA 775 95W Quad-Core Processor Model BX80569Q9550 - Retail 
Is "Intel IA-64" what I need to use for this?

> XFX GX295NHHFF GeForce GTX 295 1792MB 896 (448 x 2)-bit GDDR3 PCI Express 2.0 x16 HDCP
Supported?

---

### Post by kanikilu on 2009-03-31
You'll need the 64 bit version to use 8GB of RAM.

I'm not sure about the monitor/resolution question (my 22" widescreen works fine), but other than that, I don't see anything in that list that stands out as not being compatible.

---

### Post by 3rdalbum on 2009-04-01
8 gigabytes of RAM is overkill if you're just going to be playing WoW. Even 4 gigabytes is. I don't think even Vista could use that much, even if you had Photoshop, Lightwave, Premiere and Crysis running at the same time.

I also imagine that the graphics card is overspecced for WoW as that's pretty much a top-of-the-range GPU. You might want to check [www.nvidia.com's](www.nvidia.com's) Linux drivers page to check that the latest driver supports the GTX295; from memory I think it does, but best to make sure.

Core 2 is EMT64 (i386 with 64-bit extensions), not IA-64. So when you download Ubuntu, download the ordinary 64-bit edition, NOT the IA-64 port.

I think it should run fine, but I don't think anything on Ubuntu can really take advantage of such an OTT system. Good on you for giving yourself plenty of headroom though :-)

---

### Post by blackened on 2009-04-01
> **kanikilu said:**
> ...I'm not sure about the monitor/resolution question (my 22" widescreen works fine), but other than that, I don't see anything in that list that stands out as not being compatible.

The monitor has a max resolution of 1920x1200, which is pretty low for its size. The benefit of this is that you won't need anything near as powerful as a 295 to drive it. In fact most integrated graphics can push that resolution.

Using this machine to just play WoW is overkill, and that's putting it lightly.

---

### Post by vodkashot on 2009-04-01
> **blackened said:**
> 
Using this machine to just play WoW is overkill, and that's putting it lightly.

Overkill is what I am going for. WoW isn't the only game I want to be limited too. That is just the main game I will be playing. =)

Thank you for the input guys, appreciate it a lot!

---

### Post by albandy on 2009-04-01
> **kanikilu said:**
> You'll need the 64 bit version to use 8GB of RAM.

I'm not sure about the monitor/resolution question (my 22" widescreen works fine), but other than that, I don't see anything in that list that stands out as not being compatible.

This is not true at all, it depends on the kernel parameters not in the system architecture.

For example, I'm using ubuntu server with 16GB of RAM running at 32 bit, the kernel can use about 64 GB of RAM in 32 bit mode, but it should be enabled and recompiled.

---

### Post by vodkashot on 2009-04-01
Before I have to ask later, what is the best file system to use for Linux duel booting next to Windows?  ReiserFS?

---

### Post by j7%&lt;RmUg on 2009-04-01
Im not sure that the geforce 295 is supported on ubuntu. If you were forced to downgrade because of this then i know most things up to a 9800 GTX work fine.

8GB RAM is serious overkill and might cause some problems i would still with a max of 4GB if you ask me.

Also i would go with ext3 if you want it nice and stable or ext4 if your using jaunty and want something faster.

---

### Post by vodkashot on 2009-04-01
> **nisshh said:**
> Im not sure that the geforce 295 is supported on ubuntu.

I saw that Nvidia updated drives March 30th, But I am unsure if that driver will work fine for this video card? Anyone know, or have experience using this card with Ubuntu?

---

### Post by pg-13(prostitute) on 2009-04-01
so 4gb is the most mem i can use with 32 bit?

---

### Post by albandy on 2009-04-01
> **pg-13(prostitute) said:**
> so 4gb is the most mem i can use with 32 bit?

NO! only if you don't want to recompile your kernel.

---

### Post by vodkashot on 2009-04-01
> **vodkashot said:**
> I saw that Nvidia updated drives March 30th, But I am unsure if that driver will work fine for this video card? Anyone know, or have experience using this card with Ubuntu?

anyone?

---

### Post by blackened on 2009-04-01
Again, as to the monitor: if you're going to run at 1920x1200 then, if it were me, I would go for something in the 24" range. It will look a far sight better than the 27.5" will at that resolution.

If I were hell bent on getting a screen that large, then I would spend the money and get one that can handle 2560x1600. It'll cost you though.

---

### Post by 3Miro on 2009-04-01
All Intel and AMD CPUs are supported by Ubuntu, no issue there.

For the ram, you could run more than 4GB (actually the practical limit is little over 3GB), however, to use the full power of your system, install 64-bit OS. The 32-bit version would be slower.

Power supply should be OS independent, I expect no problems there.

Any CD/DVD device I have ever tried under Linux have worked out-of-the-box (even back in the old days 8 or so years ago). I would be shocked if there is an issue.

For the video, I would poke on nvidia.com and/or the nvidia forum to see if it is officially supported. On 1.80 it should be, but one had better check.

I have a Gigabyte Mobo, goes along with the penguin just fine. However, yours is a different model, so I don't know.

---

### Post by Slim Odds on 2009-04-01
> **albandy said:**
> NO! only if you don't want to recompile your kernel.

Not necessarily, the 32 server kernel is configured for more than 4G of memory. But it's also configured in such a way to make it less desirable for a desktop machine (different time slice, etc.).

---

### Post by albandy on 2009-04-02
> **Slim Odds said:**
> Not necessarily, the 32 server kernel is configured for more than 4G of memory. But it's also configured in such a way to make it less desirable for a desktop machine (different time slice, etc.).

Exactly! for example preemption is disabled in server kernel version.

---


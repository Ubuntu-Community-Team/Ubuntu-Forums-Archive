---
title: "I'm new  please help"
date: 2009-03-15
forum: General Help
---

### Post by tony12 on 2009-03-15
Hi!

Two weeks ago I have installed ubuntu 8.10 and I have never before even seen  a linux operating system. I am stuck on very low resolution which is 800x600(4:3). My motherboard is asus P4SGX-MX. I have downloaded  video driver for linux but I do not know how to install it. The driver is sis_drv.o-410. I've tried lots of things, even from some of the latest ubuntu books, but nothing worked. Please can someone out there be kind and help me. Please in step by step and in every detail, as I'm new to ubuntu and linux in general.

Thank you

---

### Post by chubble10 on 2009-03-15
Simply do the following:
[LIST=1]
[*]Go to System
[*]Go to Administration
[*]Click on 'Hardware Drivers'
[*]Wait for it to search for available drivers
[*]Choose one for your graphics card or whatever
[*]Click 'Enable' once you have selected the driver you want 
[*]Wait for it to download it and install it
[*]Click close
[*]You are done
[/LIST]
Or, if you don't know which driver you want, then do the following:
[LIST=1]
[*]Right click on your desktop
[*]Choose 'Change Desktop Background'
[*]Click on the 'Visual Effects' tab
[*]Choose 'Normal'
[*]It will then probably search for a driver for your graphics card so it can enable the effects. Wait until it has finished after confirming you want to install it
[/LIST]
That should be it.
Hope it helps.;)
See image attachments if unsure.

---

### Post by tony12 on 2009-03-16
Hi chubble10 and The Rest of the Linux world!

I have tried "hardware drivers" but nothing come up,it just said "no proprietary drivers are in use on this system",( I have tried that before as well). I haven't tried untill now 'Visual Effects' tab but yet again no luck. It just said tha "desktop effects could not be enabled.

So, I'm not sure what else to do. Could it be that the motherboard is to old? That it doesn't support sis driver? I don't have a seperate graphics card, video is intergrated with the mother board. Could it be that Linux doesn't support intergrated graphics?

Thank you

---

### Post by Vince4Amy on 2009-03-16
I think that the GPU on that motherboard is too old to handle desktop effects. Though you could try buying a cheap AGP Graphics  card. Wait for another opinion first though.

---

### Post by Neo_The_User on 2009-03-16
You don't need to buy anything. Where did you download the sis driver? I'll write you a guide on how to install it. It's not the repository so you'll have to do it by hand.

---

### Post by heindsight on 2009-03-16
I assume you downloaded that sis driver from the asus website. I don't think it will work - it seems it's rather old, written for XFree86 4.10

XFree86 is pretty much obsolete, everyone uses X.Org nowadays.

Basically, I doubt you'll get that driver to work.

The sis driver that's already included in Ubuntu should work with your integrated graphics card though. According to the Asus website, that motherboard uses a graphics card based on the SiS 650/651 chipset and according to the manual for the X.Org sis driver, it supports cards based on the following chipsets:
> SiS5597/5598  SiS530/620  SiS6326/AGP/DVD  SiS300/305 SiS540 SiS630/730
SiS315/E/H/PRO   SiS550/551/552   **SiS650/651**/661/741   SiS330   (Xabre)
SiS760/761 XGI Volari V3/V5/V8 XGI Volari Z7


So you shouldn't need the driver you downloaded - you already have a driver, you only need to configure it.

Unfortunately, I don't know much about how X configuration works in Ubuntu 8.10 (I understand that the newer version doesn't use /etc/xorg.conf anymore) so I'm afraid I can't be of much help in actually configuring your graphics card.

All I can suggest is to open a terminal window and run:
```
dpkg-reconfigure xserver-xorg
```
I don't know if that will help though...

---

### Post by tony12 on 2009-03-17
Hi!

Thank you all for trying to help. 

I've tried dpkg-reconfigure xserver-xorg and nothing happened.
 Shell I continue using windows?

---


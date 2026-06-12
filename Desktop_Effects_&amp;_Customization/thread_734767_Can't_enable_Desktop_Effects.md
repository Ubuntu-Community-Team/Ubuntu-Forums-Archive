---
title: "Can't enable Desktop Effects"
date: 2008-03-25
forum: Desktop Effects &amp; Customization
---

### Post by Thing2 on 2008-03-25
When I try to assign Visual Effects to anything besides "none", I get a message saying "Desktop effects could not be enabled". I have the proper driver installed and enabled for my nVidia GeForce 8600 GT video card, but all I can do with that right now is change my screen resolution. I'm using Gusty Gibbons.

What should I do?

---

### Post by uberlube on 2008-03-25
launch compiz from the terminal and post the output.

---

### Post by ad_267 on 2008-03-25
Do you have dual monitors by any chance?

Desktop effects only seem to work with TwinView and not xinerama

---

### Post by ax1m on 2008-03-25
I have exactly the same problem as Thing2.

I cannot enable desktop effects and am using an HP dv2530 with an NVIDIA Geforce 8400M graphics card.

compiz says:

> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

I have only been using Ubuntu for 24 hours and this is pretty much and out-of-the-box installation - I haven't fiddled about with any default settings except that I've tried to tell Ubuntu what graphics card I'm using but it always reverts to:

> vesa - generic VESA-compliant video cards 

I'm guessing that I need a proprietary driver, but don't know where to get one or how to tell Ubuntu to whitelist it.

Thanks in advance anyone who can help

---

### Post by mahela007 on 2008-03-25
hi I also have a problem with the effects. I had them about an hour ago but then I ran a few commands to solve the problem of incorrect refresh rate on start up. (they can be found [here]("http://www.namanb.com/2007/11/ubuntu...n-problem.html")).
after i entered those commands i have no effects. And i cant even enable them.

---

### Post by Therion on 2008-03-25
> **ax1m said:**
> I have exactly the same problem as Thing2.

I cannot enable desktop effects and am using an HP dv2530 with an NVIDIA Geforce 8400M graphics card.  ...  I'm guessing that I need a proprietary driver, but don't know where to get one or how to tell Ubuntu to whitelist it.
Install and run [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") then go to System/Administration/Restricted Drivers Manager and "Enable" the new driver. 
Then [go here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) to install CCSM (Compiz Config Settings Manager) and too get started with setting up some of the basic animations, get the Desktop Cube, etc.

If you boot to a black screen, or your screen resolution is dorked, don't panic.  You just need to edit your menu.lst file.

---

### Post by ax1m on 2008-03-25
Thanks for your reply, but I've had no luck with Envy. I think there is something fundamentally wrong with the way I've set up Ubuntu - or I'm missing a bucket of updates.

I'm going to clean install and get all the updates I can, then try again. The more I've been fiddling trying to make it work, the longer the list of missing files/broken things becomes.

I've got no work to lose on this box as I only set it up on Sunday.

I'll post again if I can't get it to work on a clean install.

---

### Post by Ub1476 on 2008-03-25
After clean install of Ubuntu, update your system:

```
sudo apt-get update
sudo apt-get upgrade
```

Now download Envy and let it install the driver and configure x for you.

If Envy says it does not recognize the card, run Envy in text-mode:

```
envy -t
```

If you have installed any previous drivers (System>Administration>Restricted Driver Manager for instance), remove those first!

---

### Post by Thing2 on 2008-03-25
> **uberlube said:**
> launch compiz from the terminal and post the output.

"compiz" returns 
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

---


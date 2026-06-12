---
title: "nvidia-glx or nvidia-legacy?"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Hi-Teck on 2006-07-23
I have a Geforce2 Ti AGP and a TNT2 PCI running my dual screens. Right now I am using the "nv" driver. I know TNT2 is the under the "nvidia-legacy" driver and I am pretty sure the Geforce2 Ti is under the "nvidia-glx". I have played around with both drives. If I install "nvidia-legacy" if kicks out my Geforce...if I install "nvidia-glx" it kicks out my TNT2. 

Is there any fix....or am I SOL...:-)
My end result is to get rid of some GUI lag when I have multiple windows opened.
I would if all possible to keep Gnome...b/c it is my fav. GUI out of the ones I have tried.

Thanks
Hi-Teck

AMD 1GHz
786 RAM

---

### Post by autocrosser on 2006-07-23
I think you know the answer to your problem---but--either stay with the "nv" driver or get a newer dual-head card--I bought a XFX GeForce 5200 256DDR AGP for 49.00 + shipping from TigerDirect--I'm sure you can find other Nvidia deals for lo-cost on the net----

---

### Post by orb9220 on 2006-07-23
Not only it's a bear to try and gonfig two cards. You have two cards that use 
different drivers.

Which means not impossible but need a linux guru to config for you. Would be a very hard task to do from instructions on a web site.

I am using an cheapie nvidia FX5200 with adapter on the dvi port so I can use two monitors.

But I can really only Have one desktop of 2560x1024 to use I could thru some tweaking know you can actually have to seprate desktops of different resolutions but the driver does not support the ability to drag apps across the displays and the mouse will not move from one to the other without doing a switch display thru the keyboard.

So at present Dual View is not supported what is supported is know as Horizontal Span mode which in my case is two monitors at 1280x1024 are merged into one desktop of 2560x1024.

It would be easier to find somebody selling a card with the dvi port on it.

---

### Post by Hi-Teck on 2006-07-24
I have just found out what I was wanting is possible and not that hard....I compliled the drivers "Latest Legacy GPU version" from nvidia.com and made some other package installs and uninstalls and BOOM we have dual head with the "nvidia" drivers....If anyone needs some help with this pm me...i wrote myself a readme so I would not forget my self.


HAPPY DAYS
Hi-Teck

---

### Post by orb9220 on 2006-07-24
Well good for you. Glad it worked out since display drivers are still a pain in the ubuntu beans.

---


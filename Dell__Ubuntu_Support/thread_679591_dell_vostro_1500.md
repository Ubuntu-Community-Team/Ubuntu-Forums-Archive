---
title: "dell vostro 1500"
date: 2008-01-27
forum: Dell  Ubuntu Support
---

### Post by Nandoz on 2008-01-27
i have successfully installed the ubuntu on my dell vostro 1500 and i am also running vista as a paralell. when it boots up ubuntu is at the top of the list how ever i want vistra to be at the top so it auto mticaly runs vista as defult when im not there to go down n press eneter on vista.

---

### Post by Ub1476 on 2008-01-27
You can try the this [app]("http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391").

GRUB is the name of the boot menu, just so you know:)

---

### Post by Fusker_The_Cat on 2008-01-28
Hi, i also have a vostro 1500, however my sound is not working, trying to load alsa mixer results in a blank window. Any sugestions?

---

### Post by Nandoz on 2008-01-28
yea my sound is not working aswell...

---

### Post by Jeff311 on 2008-01-28
Im thinking of buying the Vostro 1500 with thse specs.... 
> 
PROCESSOR == Intel® Core&#8482; 2 Duo T7250 (2.0GHz, 2MB L2 Cache, 800MHz FSB), English	
OPERATING SYSTEM == Genuine Windows® XP Home Edition, SP2, English
LCD DISPLAY == 15.4 in UltraSharp&#8482; Wide Scrn SXGA+LCD Display w/TrueLife&#8482;	
INTEGRATED WEBCAM == No Webcam Optio
MEMORY	== 1GB Shared Dual Channel DDR2 SDRAM at 667MHz, 2 Dimm
HARD DRIVE == 250GB 5400RPM SA160 Hard Drive
OPTICAL DRIVE == 24X CD Burner/DVD Combo Drive, without Roxio Creator
GRAPHICS CARD == 256MB NVIDIA® GeForce&#8482; 8600M GT
WIRELESS CARD == Dell Wireless 1390 802.11g Wi-Fi Mini Card
SOUND OPTIONS == High Definition Audio 2.0


Will it work okay, except for the sound I guess.  The things I am worried about are the graphics and wireless cards.

---

### Post by Fusker_The_Cat on 2008-01-29
I had trouble with pretty much all other versions of linux on my vostro 1500, however Ubuntu 7.10 works perfectly fines except for sound.

---

### Post by initialxy on 2008-02-01
hello guys, i have vostro 1500 myself. I have the default (cheapest) audio card and wireless card, and here is how i got my things working.

for audio:
```

sudo apt-get install linux-backports-modules-generic
sudo nano /etc/modprobe.d/alsa-base

```

then add the line..
```

options snd-hda-intel model=dell

```

to the end of the file, save, restart. now audio is working perfect for me! o by the way i have all the newest updates installed ahead of time, not sure if that matters.

for wireless:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

there, hope that helps!

---

### Post by Nandoz on 2008-02-04
yep sound works great!!!

---


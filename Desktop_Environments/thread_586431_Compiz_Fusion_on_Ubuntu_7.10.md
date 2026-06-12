---
title: "Compiz Fusion on Ubuntu 7.10"
date: 2007-10-22
forum: Desktop Environments
---

### Post by Dotan on 2007-10-22
Hello,

I searched the web for an answer and I got none. Maybe someone here could help.

I am using IBM T30 laptop with an Redaon ATI graphic card.
I have upgraded my beloved system to ubuntu 7.10 and guess what happed to my compiz?? I'll give you a hint:  It doesn't work... (simply as that)

So I read things about it on the web, saying that ubuntu 7.10 has compiz under his wings, yeah, so I went on with that and got into Preference --> Apearence --> tab called Visual Effects. I tried to enable it but it keeps on given me the same notice: "Desktop effects can not be enabled".

It doesn't even say why... ("and I about to cry...")

Please of you - How do I install the compiz fusion effects on the new ubuntu (7.10), or how do I enable it?

Thanks,
Dotan.

---

### Post by GrammatonCleric on 2007-10-22
First, are you using the default video driver or are you using one for your ati card (i.e. xserver-xorg-video-ati)?  

-GC

---

### Post by Dotan on 2007-10-22
I am using a ATI card. I think...
It says on my Administration -->  Screen and Graphics --> Graphic card -- Radeon ATI.

Is it default? I have installed it using the terminal... I think it is not default, but you tell me.
What is default? nvidia?

---

### Post by GrammatonCleric on 2007-10-22
Open up Synaptic and do a search for xserver-xorg.  There will be a green box next to the drivers that you have install.  They will look like xserver-xorg-video Can you post only the ones that are selected?

-GC

---

### Post by Dotan on 2007-10-22
ok.

to copy-paste all the green selected? Seems that there isn't a way out of it...

the X.Org X server
X.Org X server -- core server
the X.Org X server -- input driver metapackage
X.Org X server -- ELOGraphics input driver
X.Org X server -- evdev input driver
X.Org X server -- keyboard input driver
X.Org X server -- mouse input driver
Synaptics TouchPad driver for X.Org server
X.Org X server -- wacom input driver
X.Org X server -- AMD Geode GX/LX display driver
X.Org X server -- APM display driver
X.Org X server -- ark display driver
X.Org X server -- ATI display driver
X.Org X server -- Chips display driver
X.Org X server -- Cirrus display driver
X.Org X seX.Org X server -- S3 ViRGE display driverrver -- Cyrix display driver
X.Org X server -- dummy display driver
X.Org X server -- fbdev display driver
X.Org X server -- Glint display driver
X.Org X server -- i128 display driver
X.Org X server -- i740 display driver
X.Org X server -- Intel i8xx, i9xx display driver
X.Org X server -- IMSTT display driver
X.Org X server -- Intel i8xx, i9xx display driver
X.Org X server -- MGA display driver
X.Org X server -- Neomagic display driver
X.Org X server -- Newport display driver
X.Org X server -- NSC display driver
X.Org X server -- NV display driver
2D graphics driver for Poulsbo
X.Org X server -- AMD/ATI r5xx, r6xx display driver
X.Org X server -- Rendition display driver
X.Org X server -- legacy S3 display driver
X.Org X server -- S3 ViRGE display driver
X.Org X server -- Savage display driver
X.Org X server -- SiliconMotion display driver
X.Org X server -- SiS display driver
X.Org X server -- SiS USB display driver
X.Org X server -- tdfx display driver
X.Org X server -- TGA display driver
X.Org X server -- Trident display driver
X.Org X server -- Tseng display driver
X.Org X server -- Video 4 Linux display driver
X.Org X server -- VESA display driver
X.Org X server -- VIA display driver
X.Org X server -- VMware display driver
X.Org X server -- Voodoo display driver


That's it... (that was a copy-paste job I would say...)

So, What do you think should I do now?

---

### Post by GrammatonCleric on 2007-10-22
Found the following for you.   

[http://cybernetnews.com/2007/10/21/how-to-enable-compiz-fusion-in-ubuntu/](http://cybernetnews.com/2007/10/21/how-to-enable-compiz-fusion-in-ubuntu/)

Eric

---

### Post by gleadhach on 2007-10-22
I am having the same problem with my Radeon 9550 which should be supported by AIGLX and the radeon driver, yet it is not working out of the box on my fresh install of 7.10.  The radeon driver is there, glxinfo reports that dri is working, xorg.log shows that AIGLX is running, with no errors, and compiz is installed, what gives?  I tried running compiz from the cli, it complains that xgl isn't installed despite the fact that AIGLX is and that my card is black-listed, this should work natively and out of the box, well at least it does on my Mandriva and Fedora set-ups.

---


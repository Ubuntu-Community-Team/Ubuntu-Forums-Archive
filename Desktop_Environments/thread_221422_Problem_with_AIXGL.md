---
title: "Problem with AIXGL"
date: 2006-07-23
forum: Desktop Environments
---

### Post by originof on 2006-07-23
hi to all, i'm italian....my english isn't very good....  

[This]("http://www.ubuntuforums.org/showthread.php?t=145068") say that i must modify the Device section

```

Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection

```

but i have TWO device section  

```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```
so, where i add the Option "XAANoOffscreenPixmaps" ??
thanks ;)

---

### Post by adam.tropics on 2006-07-23
a thought, could you open a terminal and do

```
lspci | grep ati
```

and post the output here, as I suspect you are using the wrong guide, as that guide is for intel, and it looks like you have ati, in which case [this guide]("http://www.compiz.net/viewtopic.php?id=389") would be better.

---

### Post by originof on 2006-07-23
yeah, i have an Ati, but the tutorial that you link, is for XGL and not for AIXGL ;)

---

### Post by adam.tropics on 2006-07-23
I know, as that (XGL) is the most suitable way to get Compiz etc running on an ati card. AIGLX is the most appropriate for an Intel card.

---

### Post by originof on 2006-07-23
i know too, i tried XGL last week, and it work perfectly, but i want also try AIXGL....so...anyone know a solution or other Tutorial ? :neutral:

---

### Post by adam.tropics on 2006-07-23
Oh ok, the mist is clearing! So you know you need to stick with fglrx drivers, and by the way, for anything xgl/aiglx related it is the fgrlx bit you need to edit. But be sure to stick wih the fglrx driver.
Just try it and see. Last week I was helping someone with an intel card, and he could only get xgl, not aiglx! Sometimes it seems so new, it's a matter of finding what works for you. I would however reccomend a dig around [http://www.compiz.net](http://www.compiz.net) ,these forums, and perhaps the Gentoo and Suse forums as well if you get stuck.

---

### Post by JoWilly on 2006-07-23
The nvidia and ait commercial binary drivers do not yet support aiglx.

At this time you can get it to work only if you have opensource drivers that make 3D work on your card (like the ati 9250 or some intel cards). The ati 9600 will definitely not work.

Stick with xgl until drivers are released for your card.

---

### Post by adam.tropics on 2006-07-24
> **JoWilly said:**
> The ati 9600 will definitely not work.

I don't know which drivers were used, but there are some reports of aiglx working on a Radeon 9600 This is [one]("http://www.compiz.net/viewtopic.php?id=1184").....(once you get down the bottom of the page!). But you are absolutely right, in so much as Xgl would be much more sensible.

---

### Post by JoWilly on 2006-07-25
> **adam.tropics said:**
> I don't know which drivers were used, but there are some reports of aiglx working on a Radeon 9600 This is [one]("http://www.compiz.net/viewtopic.php?id=1184").....(once you get down the bottom of the page!). But you are absolutely right, in so much as Xgl would be much more sensible.

Would be interesting to know how he did it, because according to this it is not possible yet : [http://fedoraproject.org/wiki/RenderingProject/aiglx]("http://fedoraproject.org/wiki/RenderingProject/aiglx")

---


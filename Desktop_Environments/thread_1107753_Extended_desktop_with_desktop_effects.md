---
title: "Extended desktop with desktop effects?"
date: 2009-03-27
forum: Desktop Environments
---

### Post by sunv on 2009-03-27
Ok I am trying to get dual screen extended desktops working.  I also want the desktop effects to work.
I have been using the extended desktop for a while with no compiz effects.  I'm bored so I want them to both work.

To get compiz effects to work, i edit /etc/X11/xorg.conf and take out:
```
        SubSection "Display"
                Virtual 2304 768
        EndSubSection

```

Then when i log off and back on, I can enable compiz effects.  However I realize my second monitor is just a clone (mirror) of the other one.
So i goto screen resolution, and make them not clones but extended desktop.
This asks me to log off and on.
I do this log off and on, and when i come back, I have the extended desktop but can no longer enable desktop effects.

Can someone please help me get both?  Extended desktop and desktop effects!

Compiz-check:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

typing grep -v ^# /etc/X11/xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

---

### Post by sunv on 2009-03-27
there are bots in this forum?

---

### Post by sunv on 2009-03-27
bump please help

---

### Post by zhocchao on 2009-03-27
I don't know anything about it, but I heard compiz cannot handle Desktops larger than x(?) Maybe that's the problem.

---

### Post by sunv on 2009-03-29
bump
what do you mean cannot handle larger than x?
what is x?
I have my laptop which is has a CRT monitor connected to it.
I would like to have extended desktop (not clone) and have compiz effects enabled.
anyone can help me?
compiz works if the display subsection of xorg.conf is removed, however this also removes the extended desktop capability.

---

### Post by zhocchao on 2009-03-30
i mean this:

"For now, you must not use a Virtual setting larger than 2048x2048 (or 1024x1024 on some chips, or 4096x4096 on some others) if you wish to use compiz. DRI simply isn't supported yet for virtual resolutions greater than that."

Really don't know if that's the problem (at least I bump'd for you)

---

### Post by simtaalo on 2009-03-30
the short answer is you can't really use compiz effects with an extended desktop.

---

### Post by Freaky_Llama on 2009-04-01
What exact graphics chipset are you running?

Edit: If Intel 965 or above, check this thread: [http://ubuntuforums.org/showthread.php?t=617934](http://ubuntuforums.org/showthread.php?t=617934) It helped with my Dell D630 use dual screens extended with Compiz effects.

---

### Post by redbob on 2009-04-01
I use my laptop with a monitor connected to it. It mades me an extended screen with 1280x1824(1280x1024 from monitor and 1280x800 from laptop), with Compiz and all effects (see image). But my video card is a NVIDIA GeForce Go 7400. I think Intel could make the same or similar, since I consider Intel good quality video cards.
[IMG]http://www.mt.trf1.gov.br/imagens/dualmonitor.png[/IMG]

---


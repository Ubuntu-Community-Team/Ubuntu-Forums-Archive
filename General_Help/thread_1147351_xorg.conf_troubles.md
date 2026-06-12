---
title: "xorg.conf troubles"
date: 2009-05-03
forum: General Help
---

### Post by drakan80 on 2009-05-03
Hi all.
I've been trying to get my laptop to use its graphics card properly. I'm running a lenovo X61 (no-touchpad), and on xorg's autoconfig i always get this
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

I've tried looking up other users' xorg files for their X61's, and input just the video parts. each time, then restarted my xserver. on the restart, xserver (or is it xorg by then?) crashes and tells me it needs to run xorg in low graphics mode. from there i need to reset my xorg to it's autoconfiguation in order to be able to run properly again.

Thanks in advance to everyone! Ubuntu user for just a few months now, and loving it! hoping to get more functionality soon :D

Almost forgot to mention. I'm running Ubuntu 8.04, as I read somewhere that there were some troubles with Ubuntu 8.10 on the X61's chipset

---

### Post by delcypher on 2009-05-03
There's no mention of what video driver you want to use in you xorg.conf file! Mine doesn't have one either (I have an ati card) so I assume this is how this how the open source drivers work now (xserver-xorg-video-intel).

Make sure you have xserver-xorg-video-intel installed. ```
sudo apt-get install xserver-xorg-video-intel
```

Other than that I can't really help. I don't use intel graphics cards.

For other people looking at this problem, laptop in question can be seen with specs [here]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-68040")

Others may be able to help you if you post the output of this command. ```
lspci | grep -i vga

```

Sorry I can't help anymore than that.

---

### Post by drakan80 on 2009-05-03
Sorry, I just wanted to use my intel graphics card : 

 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
And i do have xorg's Intel drivers installed

---


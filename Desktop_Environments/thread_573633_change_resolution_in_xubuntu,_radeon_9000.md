---
title: "change resolution in xubuntu, radeon 9000"
date: 2007-10-11
forum: Desktop Environments
---

### Post by travm on 2007-10-11
I have installed xubuntu 7.04.  I cannot increase the resolution beyond 1024x768, I want bigger.  I have added the appropriate modes in my xorg.conf file, but no avail, I even seem to have resolutions available to me that are not even in my xorg.conf file, whats up with that?  they work too, but they are like 640x480 and some different sizes, none over 800x600, which is in my xorg.conf file, and then a setting called "default" which appears to be 1024 x 768.
I am using a dell latitude d600 with a radeon mobility 9000. 
I have installed beryl and have direct rendering working and the 3d effects work fine.  I am just baffled as to why I cannot change the resolution.
here are my relevant xorg.conf sections.

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "DisableGLXRootClipping" "true"
	Option "AddARGBGLXVisuals" "true"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"	"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

please help, this resolution BS is probably the biggest turn-off that linux has for me.  I have installed to try probably 5 different distributions on 3 or 4 different systems, and not once has my resolution been adjustable, and often even when I adjust my xorg.conf file it does nothing.  what gives?

---

### Post by overdrank on 2007-10-12
Hi if I am not mistaken under XFCE when you right click on the desktop and choose desktop settings and uncheck the allow xfce to manage the desktop. Hope this helps and good luck! :KS

---

### Post by travm on 2007-10-12
whoa, ok i will try that..  I just made an angry post about how 100 people are replying to dudes thread about why he doesnt like ubuntu, yet no one was helping me.
so anyway, thanks for the proof that not everyone is full of themselves with regard to their choice of software, and I have edited out the anger but the point remains.
Thanks again, will try that as soon as i get home.

---

### Post by overdrank on 2007-10-12
> **travm said:**
> whoa, ok i will try that..  I just made an angry post about how 100 people are replying to dudes thread about why he doesnt like ubuntu, yet no one was helping me.
so anyway, thanks for the proof that not everyone is full of themselves with regard to their choice of software, and I have edited out the anger but the point remains.
Thanks again, will try that as soon as i get home.

Ok thanks and keep in mind that this is a volunteer effort and not all problems are solvable. But I happen across your post and hope that my advice can help. Good luck!

---

### Post by travm on 2007-10-12
That didnt fix it.  That setting makes my entire desktop dissapear.  Through the menu I can still select display settings, yet it still only shows 800x600 and below, plus this "default" setting which appears to be 1024x768.  I want my 1280x1024, where is the love xubuntu....  Maybe if I knew more about where those settings were, I'm not afraid of commandline, just dont know where to look.

---


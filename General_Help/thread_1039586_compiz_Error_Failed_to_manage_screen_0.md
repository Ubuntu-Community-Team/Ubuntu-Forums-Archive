---
title: "compiz Error: Failed to manage screen: 0"
date: 2009-01-14
forum: General Help
---

### Post by nabeelmoeen on 2009-01-14
Hi,

I am a linux newbie, trying to get Compiz running on my fresh installation of Ubuntu 8.0.4.
I have searched and read through numerous posts on the topic but still unable to figure out what could be wrong with my setup.
The graphics card I'm trying to run on is an ATI Radeon 7500 series.
Please see below the output of Compiz and compiz-check as well as the xorg.conf file.

Appreciate any help in getting this to work.

1. **COMPIZ-CHECK**
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

2. **xorg.conf**
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
EndSection
```

3. Output of **compiz --replace**

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5157 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by gettinoriginal on 2009-01-16
Do you have envy installed ??  It is in Synaptic.  That should install your driver for your ATI card.  :P

---

### Post by overdrank on 2009-01-16
Hi and I do not believe Envy will work on that Ati card. I have a laptop with the ATI 7000 and Hardy and compiz work ok. I believe it  uses the ati driver installed by default. 
nabeelmoeen was there anymore text from COMPIZ-CHECK as I had to change the resolution to enable compiz.

---

### Post by nabeelmoeen on 2009-01-17
hi ,

inope there is no more text from compiz-check, and i tried envy...dont remember the exact error but it refused to work.
btw i think my pc and other accessories blew up due to a power surge yesterday :( so i cant check specific error msg right now

---


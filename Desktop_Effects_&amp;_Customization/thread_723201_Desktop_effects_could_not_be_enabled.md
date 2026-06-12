---
title: "Desktop effects could not be enabled"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by zephyrus17 on 2008-03-13
Just to get this straight, I have had success running Desktop Cube on this same laptop before, but after a re-format, it won't work.
I'm using a Dell 1501 with ATi Radeon Xpress 1150.

I have install xserver-xgl, which is the latest version as said in Synaptics.
I have enabled the Restricted Graphic Driver.

Running **lspci | grep VGA** gives me:
```

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

```

Running **Compiz --replace** gives me:
```

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

This is the Monitor section from my xorg.conf:

```

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```



I distinctively remember having
```

Option		"VideoOverlay"	"on"
Option		"OpenGLOverlay"	"off"

```
or something like that the last time I had Desktop Cube.
Oh, and before my reformat, I did install the video driver through some third-party program(forgot the name, though.), then installed over it with the Gutsy Restricted Drivers method.

---

### Post by NorthernLights on 2008-03-13
> Section "Extensions"
	Option		"Composite"	"0"
EndSection

I'm not sure about that, but shouldn't your option line be 'Option "Composite" "On"'  ?

---

### Post by Therion on 2008-03-13
> **zephyrus17 said:**
> Oh, and before my reformat, I did install the video driver through some third-party program(forgot the name, though.)
That would be [Envy](http://www.albertomilone.com/nvidia_scripts1.html).

And I suggest you download it and use it to reinstall your driver.  This sounds like a config issue that Envy, most likely, will sort out for you when it configures your xorg.conf file after installing the driver.

---

### Post by brainstuff on 2008-03-13
The latest ATI drivers are entirely borked as far as I can tell. I can't get a desktop, let alone 3D to work if I use them, I'm stuck with Vesa until the issue gets fixed. It's not Ubuntu-specific - I think it's to do with the PCI-E / AGP bridge thing not being detected properly or something. Probably something.

---

### Post by zephyrus17 on 2008-03-13
Right. I'll try Envy, then.

---

### Post by brainstuff on 2008-03-13
Wowsers, I got Compiz running! :guitar:

Here's what I did tonight in roughly the right order - one of these, or a combination, got it working (ideas borrowed from a zillion pages scattered about) :) 

- ran envy, uninstalled everything ATI that might be lurking from countless previous attempts
- mucked about with the default drivers under "Screens and Graphics"
- used synaptic to find any mention of fglrx (don't think there were any)
- tried manually installing ATI's 8.42.3 x86_64 package (that failed and got me into superlow resolution)
- used Envy to uninstall it
- searched the internets for my monitor model number (LG L204WT) and  xorg.conf and pasted the whole entry for monitor over my own xorg.conf (having backed it up first)
- ran a quick System Update (4 or 5 packages, couldn't see anything relating to video issues)
- ran Envy again on a whim
- Hey Presto! 

I can't even begin to guess which part of this fixed it, as I'd tried every other guide around to the letter, several times to get it going.

My only issue so far is that full-screen video gives a rather poor frame rate (never had a problem with video or 3D in Vista). I'm just starting out with Wine too, so we'll see how gaming goes...

---

### Post by zephyrus17 on 2008-03-14
I tried it with Envy, but it said something about ia32-libs missing.
I use AMD64, anyway.

---


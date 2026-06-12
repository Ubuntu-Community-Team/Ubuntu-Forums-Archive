---
title: "All games crash upon starting"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by EmperorSquirrels on 2007-06-23
Every game I have installed crashes upon startup, leaving me in a form of a low-resolution desktop (the resolution remains the same, but I can only see a small part of it on my screen at a time; like it's zoomed in. I have to pan my way around it). No matter what game it is; native, online, or what. With some games like Enemy Territory it won't crash until I choose a server to play on.

Does anyone know what's causing this?

---

### Post by po0f on 2007-06-23
EmperorSquirrels,

You might not have video card drivers that enable hardware acceleration.  Do you know what kind of video card you have?

---

### Post by EmperorSquirrels on 2007-06-23
I have an Nvidia GeForce 6600.

I thought I did have acceleration, though. I have Beryl running smoothly. Oh, and I have tried running the games without Beryl on. So that's not the problem either.

---

### Post by po0f on 2007-06-23
EmperorSquirrels,

That card should be up to playing most games.  :)

It'd be a wise choice to turn Beryl off when playing any game though.  Since you have already tried this, could you try running a game known to crash from a terminal and post the output (if any)?

---

### Post by EmperorSquirrels on 2007-06-24
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3600002
  Serial number of failed request:  82
  Current serial number in output stream:  84

```


That's the error message it gave me when I started Alien Arena in the terminal. It's all Greek to me.

---

### Post by Feba on 2007-06-24
A quick google on this subject shows people that have had luck getting games to run full screen by updating their nVidia drivers, so I imagine you either don't have any or they're disabled.

If you're using feisty, check your restricted drivers manager, maybe try envy.

---

### Post by EmperorSquirrels on 2007-06-24
Yeah, I initially had my drivers through the restricted drivers thingy (I am using Feisty). Currently, I have my drivers installed [automatically] from Envy.

Actually, should I have the restricted drivers disabled if I installed using Envy?

---

### Post by Feba on 2007-06-24
probably, yes. trying to do the same thing with multiple things tends to screw up computers. Disable the rdm drivers, and if that doesn't work, turn them back on and disable envy.

---

### Post by EmperorSquirrels on 2007-06-24
Lots of screwy stuff started happening. I have a clean install of Ubuntu on another hard drive and I pasted its xorg.conf contents into my main hdd's xorg. Here's the part that pertains to the monitor and graphics card:

```

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC E700"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600]"
	Monitor		"NEC E700"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

If I remember correctly, shouldn't there be a part about graphicsacceleration being set to true?

---

### Post by po0f on 2007-06-24
EmperorSquirrels,

If you have the NVIDIA driver installed, you need to utilize it by changing your Device section to the following:

```
Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600]"
	Driver		"**nvidia**"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by EmperorSquirrels on 2007-06-24
Okay, from what I've gathered it seems like having used both RDM drivers and Envy to install drivers has caused problems. I uninstalled the Envy drivers and disabled the RDM and rebooted. Now, RDM tells me that I do not have any devices that need restricted drivers.

Here is my current xorg.

```
Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC E700"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600]"
	Monitor		"NEC E700"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

And I can't change the "nv" to "nvidia" right now since it has no drivers to use. It just causes the GUI to fail when I boot up.

---

### Post by Gen2ly on 2007-06-24
Probably wouldn't hurt to look into your /var/log/Xorg.0.log and lookup (EE) messages.

---

### Post by EmperorSquirrels on 2007-06-24
Well I did find this.

```

(EE) AIGLX: Screen 0 is not DRI capable

```

That's the only one that pertains to this problem. The other three are Wacom-related and I'll have to mess around with that some other time...

---

### Post by EmperorSquirrels on 2007-06-24
Okay, no matter what combination of Envy/RDM drivers I use/uninstall, I always get the same result and have to disable the drivers to get a GUI to load. One error messages seems to be constant amongst them all:

```
Error: API mismatch: this NVIDIA component has version 100.14.09, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version.

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
```

And from there on it just gives me the "make sure there is an NVIDIA device plugged in" etc.
What does this mean and how can I fix it? =\

---


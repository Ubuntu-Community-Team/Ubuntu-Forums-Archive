---
title: "NVidia Drivers (non-Synaptic) trouble"
date: 2006-02-13
forum: Desktop Environments
---

### Post by holobyted on 2006-02-13
Hey all. Hopefully this is the right forum for this kind of thread.. so anyway, here goes.

I was using the nvidia-glx package and the like for my GeForce FX 5900 card, but I decided to go ahead and install the official nVidia drivers following the guide on these forums ([http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074))

After following everything, I'm stuck at 1024x768 (used to run 1280x1024 @ 75Hz) and glxgears returns a crappy fps.

This is my xorg.conf file... (Modules/Monitor/Device/Screen sections)

```


Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"1"
	Option		"NvAGP"			"1"
	Option 		"RenderAccel"		"true"
#	Option		"AllowGLXWithComposite"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30.0 - 85.0 # 28-64
	VertRefresh	56.0 - 75.0 # 43-60

	Modeline "1280x1024_75.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```


Hope you guys can give me a hand.. Thanks!

---

### Post by holobyted on 2006-02-13
Update:

I compiled my own kernel (2.6.14-cK1) and I'm still stuck. However, after reading through the forums and trying every possible way (blacklisting agpgart and derivatives, nvidia module needing agpgart, etc) I have gotten to this point:

```

dmesg | grep -i agp
[4294687.797000] Linux agpgart interface v0.101 (c) Dave Jones

```

```
dmesg | grep -i nvidia
[4294687.956000] nvidia: module license 'NVIDIA' taints kernel.
[4294687.963000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-8178 Wed Dec 14 16:22:51 PST 2005

```

...and X seems to load the driver, but doesn't respect my modeline and glxgears is slow as hell (about 10fps)

Help, anyone?

---

### Post by RAOF on 2006-02-13
What does running "glxinfo" return?  Particularly the "direct rendering" bit?

Anything interesting in your /var/log/Xorg.log.0?  You can pick out the errors with
```
grep -i "(ee)" /var/log/Xorg.0.log
```

---

### Post by holobyted on 2006-02-13
```
glxinfo | grep direct
direct rendering: Yes

```

No errors as far as grep is concerned...

[Edit: Managed to pinpoint the modelines problem... monitor was lying to graphics card about HSync/VSync...]


What do you know... it's working now... go figure. Thanks though :p

---


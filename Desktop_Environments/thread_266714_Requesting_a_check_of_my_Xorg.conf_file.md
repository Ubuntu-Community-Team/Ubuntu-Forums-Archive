---
title: "Requesting a check of my Xorg.conf file"
date: 2006-09-27
forum: Desktop Environments
---

### Post by LostJot on 2006-09-27
I've been trying to configure so that I can use my external monitor alongside my laptop screen. Fiddled about in Xorg and got what I think will (hopefully) work. But I've heard all sorts of stories about X failing to load and causing all sorts of havoc. So before I save the changes with sudo can someone check this to see if it is likely to work/fail to load?

I've not touched anything prior to the Device sections (Input Devices and what-not), so I've not included it.

```
Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go] 0"
	Driver		"nv"
	BusID		"PCI:1:0:0"
        Screen           0
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go] 1"
	Driver		"nv"
	BusID		"PCI:1:0:0"
        Screen           1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go] 0"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go] 1"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerFlags"
            Option "Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Double Layout"
	Screen		"Main Screen"
            Screen 		"Second Screen" RightOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

The parts I'm most unsure of are the ServerFlags (is it really needed) and ServerLayout.

I'm using default nv driver, so I can't use Twin View at the moment, just Xinerama.

---

### Post by pseudonym on 2006-09-27
I didn't know the nv driver supported multiple monitors? Accordting to the [manpage]("http://www.xfree86.org/4.4.0/nv.4.html") it doesn't.

Unless something has changed very recently, I think you're going to need to install the nvidia driver for that to work.

FYI, the config looks OK, except you need to make the 'Screen' lines in 'Server Layout' look like this -

```
Screen		0 "Main Screen"
      Screen 		1 "Second Screen" RightOf "Main Screen"
```

---

### Post by powder on 2006-09-27
You are missing keyboard and mouse.  Did you leave those out?

---

### Post by LostJot on 2006-09-27
I was planning to use nvidia eventually, it's just that I do all my installing offline right now, and I can't find where the driver is at [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)

Thanks :)

---

### Post by LostJot on 2006-09-27
I think I've found what I need
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762%2b2.6.15.11-3_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762%2b2.6.15.11-3_i386.deb)

If I use this driver...

I change "nv" to "nvidia"
Do I enable Twin View in the same way as Xinerama?

And then sudo and save Xorg.conf....

?

Edit: And I'll use this to make sure I've got the new driver listed properly everywhere
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1_-_OFFLINE_INSTALLATION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1_-_OFFLINE_INSTALLATION)

---

### Post by pseudonym on 2006-09-27
For all your nvidia X config needs, go [here]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/index.html").

That's for the latest version of the driver, but I've attached an earlier text version if you are going to do this offline. The setup options for twinview and whatnot haven't changed, I don't think.

---


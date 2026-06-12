---
title: "nvidia, glxgears, and AGP"
date: 2005-08-07
forum: Desktop Environments
---

### Post by rosslaird on 2005-08-07
I'm using the nvidia 7174 driver on my system. Here are some further details:

> 
cat /proc/driver/nvidia/agp/status && cat /proc/cpuinfo | grep MHz
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
cpu MHz         : 1392.708


In my BIOS, the AGP setting is 8. Why doesn't X pick this up? Also, my frame rate is down around 400 in glxgears, which seems awfully slow. (I remember that in gentoo it was up to about 6500.) Is there a way to speed this up?

Relevant bits of xorg.conf:
> 
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"RenderAccel"		"true"
	Option		"IgnoreDisplayDevices"	"CRT, TV"
	Option		"NvAGP"			"1"
	Option     	"AllowGLXWithComposite" "true"
> 
Section "Extensions"
	Option		"Composite"	"Enable"
	Option		"RENDER"	"Enable"

Also, I notice that on boot I get a message about the nvidia-agp module being blacklisted. Is that important in terms of the framerate issue?

Thanks in advance for any tips or assistance.

Ross

---

### Post by jasmuz on 2005-08-07
Have you tried running glxgears without the composite & and render extensions disabled, some people have been getting lowsy framerates because of this.

---

### Post by rosslaird on 2005-08-07
When I disable the composite and Render extensions and turn off RenderAccel (I usually have that off anyway, since it often crashes my system), my frame rate drops to about 100.

---


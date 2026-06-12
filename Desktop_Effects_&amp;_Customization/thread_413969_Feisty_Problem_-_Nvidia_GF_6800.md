---
title: "Feisty Problem - Nvidia GF 6800"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by lunchtimemama on 2007-04-19
Beryl worked great on Edgy but I just upgraded to Feisty and I'm having some issues.

I've got an Nvidia GeForce 6800 and I'm using the driver from the Restricted Drivers Manager. When I try to enable desktop effects with the Desktop Effects app, the window borders flash for a bit and then I get the message "Desktop effects could not be enabled." When I try to start beryl (via beryl-manager), the Beryl splash comes up (at a very low framerate) and then the screen goes totally white, except for the mouse cursor.

Here's some of my xorg.conf file:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
        Option 		"XAANoOffscreenPixmaps" "True"
	Option		"NoLogo"	"True"
EndSection

...

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

I've also tried installing the nvidia driver with the unstable 0.9.2 release of envy. Same problem.

---


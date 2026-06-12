---
title: "Boot Up Problems"
date: 2009-01-30
forum: General Help
---

### Post by BlakeJustBlake on 2009-01-30
Yesterday I got some updates and then restarted my computer. After restarting and going through the Ubuntu loading screen it just went to a black screen with the loading cursor. I thought perhaps there was an X problem. So I tried Ctrl-Alt-F1 and it gave me a login prompt and after logging in I tried starting x. It gave me the following errors:

(EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics Hardware
(EE) PreInit failed for input device "Synaptics Touchpad"

So I went to my xorg.conf file and changed

Section "Device"
	Identifier	"Configured Video Device"
EndSection

To:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

The Nvidia error didn't come up next time but x still won't start and it still gives me the Synaptics Touchpad errors. In xorg.conf and all of the backup files it says the same thing for the "InputDevice" section:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

But I've never had this problem before. Any help? Is it possible not an X problem?

I alo tried doing dpkg-reconfigure xserver-xorg and it didn't help.

---

### Post by Yellow Pasque on 2009-01-30
Do you even have a Synaptic Touchpad device?

---

### Post by BlakeJustBlake on 2009-01-30
Actually, I think it's an Elantech.

---


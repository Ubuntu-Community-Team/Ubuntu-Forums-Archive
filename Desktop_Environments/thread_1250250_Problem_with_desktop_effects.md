---
title: "Problem with desktop effects"
date: 2009-08-26
forum: Desktop Environments
---

### Post by Regenerate on 2009-08-26
Hi All,

I've installed Ubuntu 9.04 on my Acer Aspire 5633WMLI laptop and Visual Effects (set to 'Extra') and compiz effects (like the desktop cube and rotation) all worked great. After connecting a external monitor however, the Visual Effects is now set to 'None', compiz effects don't work anymore and I cannot enable these anymore. When I try enabling the Visual effects I get a pop-up with the notion "Desktop effects could not be enabled". Disconnecting the monitor and restarting the laptop doesn't make a difference: all effects are disabled and stay that way. Working without the effects makes gnome much less user friendly, scrolling through (web)pages is now quite a shocky experience, not great to work with.

When the external monitor is connected, xorg.conf looks like this:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Since the effects do work fine with one monitor, I don't think this is a hardware limitation, but correct me if I'm wrong :).

So my question is: how to re-enable the desktop effects, preferably also when the external monitor is connected. If you need me to provide more information, please ask.

---

### Post by Dullstar on 2009-08-26
I know once I couldn't get my cube to work, and I found that I had accidentally turned off Rotate Cube.  Did you accidentally turn any off?

---

### Post by Regenerate on 2009-08-27
> **Dullstar said:**
> I know once I couldn't get my cube to work, and I found that I had accidentally turned off Rotate Cube.  Did you accidentally turn any off?No, settings in compiz don't work at all so that is not the problem.

Anyone else with some suggestions?

---

### Post by StonedGiant on 2009-08-28
> **Regenerate said:**
> 
After connecting a external monitor however, the Visual Effects is now set to 'None', compiz effects don't work anymore and I cannot enable these anymore. When I try enabling the Visual effects I get a pop-up with the notion "Desktop effects could not be enabled". Disconnecting the monitor and restarting the laptop doesn't make a difference: all effects are disabled and stay that way. Working without the effects makes gnome much less user friendly, scrolling through (web)pages is now quite a shocky experience, not great to work with.

I have EXACTLY the same problem. Funny thing is... everything worked fine about a month ago when I used my external monitor last. I'm glad to hear I'm not the only one with this problem. It really makes Gnome and Firefox very painful to use.

---

### Post by kerstd01 on 2009-09-26
I had the exact same problem, after examening the ../X11 folder I found out that ubuntu made a backup of my xconf.org with the exact time of the change added to the filename. I simply renamed that file to it's original name (xconf.org), after a reboot everything was working as it should.

xorg.conf after connecting external display (visial effects could not be enabled):

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2424 1388
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection


xorg.conf before connecting external monitor (with working visual effects):

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---


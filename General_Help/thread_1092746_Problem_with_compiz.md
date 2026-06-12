---
title: "Problem with compiz?"
date: 2009-03-10
forum: General Help
---

### Post by DaEMoN390 on 2009-03-10
I'm having a problem when I use certain features with compiz such as ring switcher or the cube. I don't know where to start but, if it helps I don't have any drivers listed in my administration > hardware drivers. Running lspci shows I'm using the intel 945gm. My resolution is 1280 x 800 and it happens even if I change it to something lower.
Here are the problems I'm having:
[IMG]http://s174.photobucket.com/albums/w86/CARBON_GSXR/th_RING.png[/IMG]
[IMG]http://s174.photobucket.com/albums/w86/CARBON_GSXR/th_cube.png[/IMG]

This is what my xorg.conf looks like:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Any direction would be much appreciated.

---

### Post by Neo_The_User on 2009-03-10
Add this to your xorg.conf file under section device:

```

    Option "VideoOverlay" "off"
    Option "OpenGLOverlay" "on"
    Option "TexturedVideo" "off"

```

---

### Post by jdoliner on 2009-03-10
Perhaps I'm being silly but those pictures don't make a "problem" clear to me at all, looks like compiz to me. Could we get some bigger ones?

---

### Post by DaEMoN390 on 2009-03-11
> **Neo_The_User said:**
> Add this to your xorg.conf file under section device:

```

    Option "VideoOverlay" "off"
    Option "OpenGLOverlay" "on"
    Option "TexturedVideo" "off"

```

I tried this and still no joy.

>  Perhaps I'm being silly but those pictures don't make a "problem" clear to me at all, looks like compiz to me. Could we get some bigger ones?

Sorry about that. Hope this is a little better.

---

### Post by DaEMoN390 on 2009-03-11
*bump

---

### Post by DaEMoN390 on 2009-03-14
bump :(

---

### Post by DaEMoN390 on 2009-03-16
I figured out what the problem was. It was within compiz

---

### Post by orlox on 2009-03-16
If you solved you're problem, you should mention how you did in case others get similar problems...

On the other hand, this might be related with serious performance issues with intrepid, wich seem to be getting fixed on jaunty.

---

### Post by DaveG825 on 2009-03-17
I'd be interested to know exactly what was wrong with compiz, and what you did to fix it. I think I have a problem akin to yours.

---


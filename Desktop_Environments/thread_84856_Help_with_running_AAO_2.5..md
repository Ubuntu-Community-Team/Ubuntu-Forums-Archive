---
title: "Help with running AAO 2.5."
date: 2005-11-01
forum: Desktop Environments
---

### Post by skoen on 2005-11-01
Hi.

When i try to start Americas army 2.5 all i get is the splash screen then it dissapears.

And this is what it says when i run "sh armyops"

skoen@Norbeck:~$ sh armyops
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error


How do i fix this?

---

### Post by gamesmad on 2005-11-02
sudo sh /install-dir-here/armyops/armyops

I have to run the game as root to get it to work.

Will

---

### Post by bryan986 on 2005-11-02
try uncommenting or adding

```

Load	"dri"

```

to the modules section of your xorg.conf

```

Section "Module"
	#Load	"GLCore"
	Load	"dri"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

```

---


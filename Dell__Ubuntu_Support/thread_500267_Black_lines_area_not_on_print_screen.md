---
title: "Black lines area not on print screen"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by drapaki on 2007-07-13
on an inspiron 8600 widescreen, i try to run 1440x900 (listed as an option on my xorg.conf) and all is well except i get this funny area on the left of my screen.  about 1.5 inches is shaded black... worst part is when i do a print screen, it doesn't show up. 

so i'll try and attach a photo.  

this doesn't happen on other settings... say 1280x800 (not listed on my xorg.conf!).  any ideas?

---

### Post by loserboy on 2007-07-13
that's weird, it looks like the interlacing is not working right on that portion... like it's only half interlacing. Have you ever run that high of res in a different OS?

---

### Post by drapaki on 2007-07-13
nope.. just got this laptop and wanted a linux only machine... so now i'm linux 99.9%.  (have an older machine w/ XP on it).

sorry... went off topic a bit..

---

### Post by loserboy on 2007-07-13
hmm, maybe try looking at hardware specs for that screen, maybe xorg is forcing to go out of range or whatever it's called....thats just a guess, you could also play with refresh rates, but I doubt that will help

---

### Post by drapaki on 2007-07-13
if i go higher to 1920x1200 it goes away!

---

### Post by loserboy on 2007-07-13
no clue.... but you must have eyes like a hawk... i would have to put my face into the screen to read at that res

---

### Post by drapaki on 2007-07-13
> **loserboy said:**
> no clue.... but you must have eyes like a hawk... i would have to put my face into the screen to read at that res

LOL!  yeah.. i'm still young.. only a matter of time....  :cry:

---

### Post by loserboy on 2007-07-13
why don't you go ahead and post your Xorg, maybe we can see something from that

---

### Post by drapaki on 2007-07-13
tired to leave out the stuff you don't need... i'm on 1280x800 and if i remember correctly, the black area shows up on the login screen but then goes away..

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

```

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

[unrelated]
i'm also trying to do the "two fingers on the touchpad moves the browser back" thing, if anyone knows an easy way.. (like the macs)

---

### Post by loserboy on 2007-07-13
found 2 links that might be helpful,  i can't read them fully atm so i'm just gonna go ahead and post them

[http://ubuntuforums.org/showthread.php?t=500034&highlight=black+bar+on+screen](http://ubuntuforums.org/showthread.php?t=500034&highlight=black+bar+on+screen)

[http://ubuntuforums.org/showthread.php?t=497613&highlight=black+bar+on+screen](http://ubuntuforums.org/showthread.php?t=497613&highlight=black+bar+on+screen)

edit: do you have a manual with the hardware specs of that screen (refresh rate, Hsync/Vsync, max res)?

---

### Post by drapaki on 2007-07-14
i may just try to settle w/ 1280x800.  i really don't want to take the chance of loosing my neat, light desktop effects.

---


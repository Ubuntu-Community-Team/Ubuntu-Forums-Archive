---
title: "Title wave"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by billgoldberg on 2008-01-28
I want to enable the "title wave" effect that is in "water effect" option from the compiz fusion effects manager.

But for some reason it's greyed out.

[[img]http://xs223.xs.to/xs223/08051/screenshot-compizconfig_settings_manager766.png[/img]](http://xs.to)

I'm using an ati radeon xpress 1100 hyper memory 384mb card (or so it says on the stickers on the pc).

The xorg.conf file (if it is relevant at all to the problem):

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection
```

I'm running gutsy gibbon by the way.

So how do I get this effect working?

---

### Post by Ub1476 on 2008-01-28
Click on it (double-click maybe) and set a new key for it:)

---

### Post by billgoldberg on 2008-01-28
Nope that won't work, it only brings up the system bell thing.

---

### Post by Ub1476 on 2008-01-28
You can try to run the manager from the terminal, and see what errors it gives you.

```
ccsm
```

---

### Post by billgoldberg on 2008-01-28
No error at all.

Everything else works, I just can't select the title windows. I've done some searching and there are others with the same problem (no fixes mentioned).

---

### Post by PinkFloyd102489 on 2008-01-28
Same happens to me, can only select system bell.

Im running a GeForce 5200FX with the latest driver from the Nvidia site.

---

### Post by overdrank on 2008-01-28
HI and please correct me If I am wrong but I thought that feature was disabled in Gutsy due to instability.

---

### Post by rune0077 on 2008-01-28
> **overdrank said:**
> HI and please correct me If I am wrong but I thought that feature was disabled in Gutsy due to instability.

Yeah, I think that's the case. It is there, but it was intentionally disabled because it "isn't quite there yet," or some such.

---

### Post by billgoldberg on 2008-02-04
It seems to work fine on videos I've seen (like the one from the sabayon linux live cd)

How could I reinstall that plugin?

---

### Post by FuturePilot on 2008-02-04
A lot of features like this have been disabled due to stability problems. To enable them you would have to compile it from source.

---


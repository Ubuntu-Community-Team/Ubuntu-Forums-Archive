---
title: "[SOLVED] bad resolution"
date: 2008-05-27
forum: Desktop Environments
---

### Post by embolalia1187 on 2008-05-27
**TO GOOGLERS:**
Your best bet with this problem is a new screen. Sorry. But I could not find any way to change the refresh rate without crashing the computer. As it turns out, that screen was one of few that don't support that refresh rate/resolution combination. I got a new one from newegg.com for about $140 after shipping.

Now to the original thread:
I think this is the right spot to put this, but I'm not sure.

Anyway, my XP box's HD failed, so I put in a salvaged drive and put Ubuntu 8.04 on it. It runs like a charm, most of the time. But the resolution is 1280x1024, and I can't change it to the screen's 1440x900 intended resolution. I have worked with Ubuntu a little before, a year or two ago. But I have no idea how to fix this. I seem to have narrowed down it has something to do with xorg.conf? But I edited that and it did nothing.

GFX card is Intel Graphics Media accelerator 900, which I think is the Intel 82915G/82910GL Express Chipset Family.

And here's my original xorg.conf: (all the stuff after the # lines)
```
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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
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
EndSection
```

Thanks in advance for any help!

---

### Post by Grognot on 2008-05-28
You can try adding the highlighted part to your screen section
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        [color=red]DefaultDepth    24
        SubSection "Display"
        Depth 24
        Modes "1440x900"
        EndSubSection[/color]
EndSection
```
I have a feeling you may need to install the driver though.

---

### Post by Grognot on 2008-05-28
If that doesn't work you can try installing the driver with
```
apt-get install xserver-xorg-video-intel
```
and set the driver in your xorg.conf to "intel" from your default "vesa".

---

### Post by embolalia1187 on 2008-05-28
Okay, I did all that. It took me a while, and I had about fifteen bajillion problems along the way, and it's still not letting me do widescreen. I have more options for resolution, but not 1440x900.

Final edit: Turns out a different screen of the same size and resolution worked. Apparently my old one just didn't like that refresh rate.

---


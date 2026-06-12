---
title: "Nvidia driver - Display remains blank after it goes to sleep"
date: 2008-07-08
forum: Desktop Environments
---

### Post by firsttry on 2008-07-08
Hello,

I've just made a fresh install of Hardy on my laptop, and I'm having an issue with the power saving mode - I also had this with Feisty and Gutsy (same laptop, initially tried an upgrade but the problem stayed, thought a fresh install might magically fix it, but no...).

Basically once the display goes to sleep moving the mouse or pressing buttons does not bring it back any more - I know for definite that Ubuntu still works as I can reboot by typing sudo reboot into a new terminal window, though i can't see anything - the screen comes alive again after it boots.

Anyway lspci gives me:
```
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 460 Go] (rev a3)
```

... and I'm running the nvidia driver (from xorg.conf)
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"UseDisplayDevice"	"DFP-0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection
```

The config is pretty much all by Ubuntu itself besides the DFP-0 line, which I had to add in order for the driver to display stuff correctly (EDID could not be auto-detected).

I had a look through my dmesg too but nothing struck me as particularly odd, so I won't spam this thread with dmesg stuff (yet?), and as far as I can see the X log seems fine too... but I'll be happy to post stuff if anyone thinks they could be useful.

Obviously one workaround would be to not put the display to sleep at all, but that's hardly a solution :)

Some help would be much appreciated!

Thanks!

---

### Post by sdennie on 2008-07-08
Two things you could try:

1) When the screen is blanked, try hitting Ctl-Alt-F1, wait a second and then hit Ctl-Alt-F7.

2) If it's a laptop, and it has TV/VGA out, try hitting the button combination that toggles that a few times.  For me it's Fn-F8 but, it's likely different for you.

---


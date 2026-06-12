---
title: "Force resoultion"
date: 2008-08-29
forum: Gaming &amp; Leisure
---

### Post by linuxguymarshall on 2008-08-29
I want to play some games on my 19" HDTV on my desk. The only problem is that when I want to play anything in a 4:3 (Standard) format it says "Invalid Format". However it will play anything in a 16:9 (Widescreen) format. This is a problem for some games like DOOM 3. So how can I force them to run at a certain res? BTW, I don't mind the distortion

---

### Post by crispy_420 on 2008-08-30
I'd like to know as well. I have the same type of issue as well. 

Maybe a location of config files to change resolutions available?

---

### Post by Crafty Kisses on 2008-08-30
Post your X.org

---

### Post by crispy_420 on 2008-08-30
I assume you just need the video display parts:

> Section "Device"
	Identifier	"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Module"
	Load		"glx"
	Load		"evdev"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640×480"
	EndSubSection
EndSection

---

### Post by crispy_420 on 2008-08-30
OK, I solved it for myself.

I ended up looking at the situation from a step back.

My resolutions were correct for what the monitor could do. CHECK
My refresh rates (horizontal and vertical). NOT SURE

So went to manufacturers website. 

My xorg was off. Tweaked and rebooted. 

Only tried frets of fire and it worked for me. I will test other games to see results of said tweak and report back with what I find.

---

### Post by crispy_420 on 2008-08-30
Update:

That seemed to work for me. Tried a few FPS and all is fine.

---


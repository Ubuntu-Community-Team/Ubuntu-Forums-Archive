---
title: "Dual Head Ati Radeon 7000 Monitor Blinking"
date: 2009-03-16
forum: General Help
---

### Post by yashima on 2009-03-16
Hi,

I upgraded from Hardy to Intrepid today. I am having trouble getting my second screen working properly. The graphics card is a Ati Radeon 7000 - it is using the generic driver, as the current Ati drivers don't support cards this old anymore. I have two 17" screens connected to this.

I have a "Virtual" directive in my new Intrepid xorg.conf and I managed to use the new display configuration utility to arrange the two screens next to each other by turning of the Mirror Screens flag. Now there are but two problems: 

A) the "slave" screen keeps blinking on and off for a second (like a graphics mode change) irregulary, f.e. when starting up new applications, or when clicking on links in firefox or when switching windows - but not every time I do any of these things. 

In another thread - concerning nvidia drivers however - there was a suggestion to turn of "regular randr checks for monitor changes" and indeed that is what this behaviour looks like but there is no randr process running on my system. The menu in the Service Manager does not have any option for turning off any randr checks either, am I missing something here?

B) I cannot move windows completely onto the right screen, they seem to "hang" on the left screen with a couple of centimeters? The amount of "hang" on the left screen is a fixed size and I can move my mouse pointer all over the screen, I just cannot move any windows all over. 


I am not sure these problems are connected but they keep me from being able to work with this set-up. I cannot provide my xorg.conf at this moment - since this is about my work computer. I will add it in the morning. I would be very happy regarding any hints to a solution to this problem. Thanks in advance from anotherwise very happy ubuntu user :)

Bye
Yashima

**UPDATE: This was a hardware problem, I got a new graphics card and now everything is fine. Too bad this came at the same time as my Intrepid upgrade otherwise it would have been more obvious.**

---

### Post by chewit on 2009-03-16
Hi,

I am using a ATi Radeon 7000 card (PCI 64mb) on 8.10 . I am using the ati driver, 'ati' from xorg.

what driver are you using at the moment?

---

### Post by yashima on 2009-03-17
I am using "radeon" - I was having trouble with the dual head installation and changed it from "ati". But I was having the blinking behaviour before the change. The installed driver is the xorg package - I just changed the identifier in the xorg.conf.

---

### Post by yashima on 2009-03-17
This is the xorg.conf on my system after a dpkg-reconfigure.

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

Here's my old one (except all the "Hal is now used - comments")

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Belinea"
	Vendorname	"Belinea"
	Modelname	"Belinea 10 17 50 / Art. No. 111732"
	Horizsync	31.0-83.0
	Vertrefresh	56.0-75.0
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Belinea"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2560	1024
		Modes		"1280x1024@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

I have the same weird behaviour in both cases. 

Bye Yashima

---


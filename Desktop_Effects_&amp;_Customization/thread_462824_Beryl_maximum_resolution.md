---
title: "Beryl maximum resolution?"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by boenils on 2007-06-03
Hi I'm using Kubuntu 7.04 Feisty Fawn and I think it's great: most user-friendly distro I've ever seen and awesome online support! I got Beryl working on my ATi mobility radeon 9000 (r250) M9 and It's been doing great, but I'm forced to work on a resolution of 1024x768, which I think is a bit too low (the letters on my screen are awfully big and I have to scroll down and left in almost every window). If I choose a higher resolution, beryl works fine but it only covers the screen partially (to the right I get nothing, only traces of windows I have moved over the right part of the screen).

Is there any way to fix this, please keep it simple, as I am still a bit of a newbie. Especially when it comes down to the console ;)

Hope I didn't post wrong or something, as it is my first :)

Thanks in advance...

---

### Post by patrickfromspain on 2007-06-03
probably a drivers issue.. your card isn't that good and ati drivers are terrible.

---

### Post by boenils on 2007-06-03
Any suggestions on installing another driver? Because Beryl and Compiz do work on this card in higher resolutions, I figured that out using the Mandriva 2007 Spring live-cd. And how do I know which driver I have installed?

---

### Post by Rocket2DMn on 2007-06-03
I have the same video card in my Dell 600m laptop.  I followed this guide when setting up Beryl for myself after I couldn't get dual head to work (turns out its no longer possible with our card)
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

Re-setting up Beryl might help, but no guarantees.

Make sure under the Screen section in "/etc/X11/xorg.conf" the correct resolutions are declared for your depth.  Here is that portion of my xorg.conf

> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Laptop Screen"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Good luck!

---


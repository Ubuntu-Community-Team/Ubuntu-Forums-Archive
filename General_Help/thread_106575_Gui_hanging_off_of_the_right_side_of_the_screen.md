---
title: "Gui hanging off of the right side of the screen"
date: 2005-12-21
forum: General Help
---

### Post by blacklantern on 2005-12-21
I've just installed ubuntu, and I love it so far - I just have one issue. For some reason, GNOME is hanging off of the right side of the screen. It's not by that much, but just enough to be annoying. To give you an idea, when I set a panel on the right side of the screen and place a set of geyes on it, the right eye is nearly cut off. Not a very big deal, I suppose, but if anyone has an answer, please don't hesitate to respond.

---

### Post by roachk71 on 2005-12-21
[LEFT]blacklantern,

First, a few questions need to be asked, since you didn't provide details in your post:

1: What type of monitor are you using (LCD or CRT)?
2: How big is the monitor?
3: and what is its maximum resolution (if you have that information right off)?

If it's an LCD and you have the other two answers, open a terminal window and type the following:

```

sudo dpkg-reconfigure xserver-xorg

``` 
and follow the instructions it presents. Be careful with the answers you give to its questions, however (the default choices are usually best): some of the options available can crash the X server, and even cause the machine to hang.  This information is also helpful with good ol' CRTs.

I had to reconfigure my X server for my Gateway 2000 Vivitron 17 monitor; maybe these instructions can aid you a bit.

Oh, by the way, after reconfiguring, you'll have to log out of GNOME and restart Xorg by using Ctrl-Alt-Backspace.

If it's a CRT, and it doesn't have a complete array of display controls, let me know in your next post. There's a package to help with that problem; I simply can't remember which right now since I'm up past bedtime and pretty tired.

Update: I just tried the same applet at that position. If in fact all else is well with your screen, try right-clicking on the panel and left-clicking on properties. Then adjust the size of the panel from there.
[/LEFT]

---

### Post by Ocxic on 2005-12-21
chack that you have the monitor itself set correctly, cause u can change the size of the screen using the buttons/menu on the monitor itself.

---

### Post by blacklantern on 2005-12-21
[QUOTE=Ocxic]chack that you have the monitor itself set correctly, cause u can change the size of the screen using the buttons/menu on the monitor itself.[/QUOTE]

*facepalm* The auto-adjust worked. I should have tried that before anything. Thanx to the both of you. *laughs*

---

### Post by javaman67 on 2005-12-21
What theme are you using?  I can't remember which one, but just recently, I checked out a new theme and it kept shifting to the right side and you had to maximize the window to make it line up correctly.  Try a different theme.

---

### Post by handy on 2005-12-21
The correct screen refresh rates can solve this problem for CRT monitors too.  Ubuntu, it would seem mostly does not auto detect your monitor, so when you look at your "System/Preferences/Screen Resolution" menu, your monitor "Refresh Rate" will be "60 Hz" with no other options in the drop down.  

**Always make a backup of any configuration files *_BEFORE_* you edit them, know where you saved it & what you called it.**  I just add ".bak" to the end of it & save it in the same directory.

You can edit the xorg.conf file inputing the correct ranges will have positive effects in the visual stability of your display, this is more noticeable on some monitors than others, & by some people more than others, ie.  Some can't detect a difference, others have watery eyes or even headaches due to the fine quiver of slower refresh rates.

If you don't have a manual, go to your screen manufacturers site if you can.  If no go with manufacturer, googling should do it.  

Edit the the "HorizSync" & the "VertRefresh" settings in xorg.conf.  Don't change the "Identifier" value.  Mine looks like this:

======================
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-107
	VertRefresh	48-120
EndSection

======================

While your in xorg.conf, if you have newly installed Ubuntu, & you are not happy with the limited screen resolution.  You can input a higher res'.  Be careful that you don't exceed your display chip, or your monitors capabilities.  If you do X won't run.

Change only the "Modes" value, if your xorg.config has more than one value, e.g. "Modes    "640x480" "800x600" "1024x768""
You are best off just setting the one  highest value, Ubuntu won't get confused.

A copy of this section of my xorg.conf follows:

======================
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

======================

I hope this helps someone out there,  oops, I nearly forgot  :KS 

Cheers,

handy

---


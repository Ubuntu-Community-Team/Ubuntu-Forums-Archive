---
title: "Can I &quot;train&quot; my desktop?"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by bohsocks on 2007-08-25
Hey folks.  I have a dual monitor setup with Gutsy.  The 2nd screen is a TV to the left of my   monitor (for full screen video).  So I setup my xorg.conf to put the 2nd desktop to the left of my main one (makes sense).

The problem is that everything that goes to the desktop (downloaded files, shortcuts) goes to the TV's desktop.  When I'm using my TV it's a pain to have to switch over to drag an icon..... is there any way to make my desktop know to put new icons and files on a specific desktop and/or position?

Thanks.

---

### Post by boolean10 on 2007-08-26
Are you usuing KDE or Gnome?

---

### Post by buschi on 2007-08-26
hi there!

i have no experience with that, just read a bit ... something similar was discussed at [http://ubuntuforums.org/showthread.php?t=149976]("http://ubuntuforums.org/showthread.php?t=149976") . what happens if you put the TV right of the screen? and what happens if you do not use LeftOf but Relative? which screen do you define first in your xorg.conf?

good luck,
sebastian.

---

### Post by bohsocks on 2007-08-27
Hi! Thanks for your responses!

First of all, I am using gnome.

And buschi, yes.  I had originally had the screen to the right of my main desktop.  But since the TV itself is physically to the left, I would prefer to have it where it belongs.  When I did it with the RightOF, it worked fine.  

But it seems the icons just go to where they think they should "logically" go.  For example, if I had put the second screen as "Above" I think I would have the same problem.

Here is the relevant section of my xorg.conf file.

```

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS, CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1280x800-800x600" #Monitor Resolutions for Primary-Secondary monitors
Option "MergedNonRectangular" "true" 
Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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

```

Also, I was just wondering... when you say "Relative".... does that mean it's possible to make my 2nd screen in a more arbitrary place like a X/Y Axis number?  What I mean is....

My first screen resolution is 1280x800 (wide) and my second is 800x600....which means my desktop wallpaper is 2080x800... with the top left being my TV, the whole right being my main, and the bottom left having just black.... is it possible to do something like "LeftOf,Below" so that it is LeftOf my main screen but vertically aligned to the bottom of my main screen?  I've attached my wallpaper for a visual.

---

### Post by buschi on 2007-08-27
hey!

you know, i was thinking that things go either to the most upper left -- or to screen 0. as you say things work fine when you give RightOf, the former seems to be true... but (as i am new to this stuff i may be wrong) shouldn't there be two "Screen"s in your xorg.conf, one having devid 0?

perhaps you can find something useful in [http://xfree86.org/current/XF86Config.5.html#sect11]("http://xfree86.org/current/XF86Config.5.html#sect11") .

best,
sebastian.

---

### Post by bohsocks on 2007-08-27
Well when I set up my xorg.conf file, I had a lot of trouble..... mainly because I had trouble finding a way to do it with a TV, and not a second MONITOR.... as far as the drivers go and stuff.

So it was a lot of trial and error and until I got it working... I'm not entirely sure how it works... but it does.  That's why editing it is also so iffy.  Usually all I touch is the above, below, rightof, leftof thing.....

Trust me, there's so much more I'd like to do with it.... but I don't know how.  And I'm sure I have things in there I don't need, and it's not as "efficient" as it could be... but since it works, I'm happy.

---

### Post by buschi on 2007-08-27
as far as i understood, it doesn't work..... ;)

did you take a look at the link? it explains the relative-thing.

---

### Post by bohsocks on 2007-08-27
Yes I did, thank you.  I am using it right now to hopefully re-work my xorg.conf

Hopefully I can find my original xorg.conf so I can try this again the right way.  (I also want to get Compiz working, which it does not right now).

---

### Post by bohsocks on 2007-08-27
Update.... I'm reworking my brand new xorg.conf.... and I can't get anything to work with multiple screens/monitors/devices.... this is so frustrating!

---

### Post by buschi on 2007-08-29
hey there -- how is life? doing progress?

---


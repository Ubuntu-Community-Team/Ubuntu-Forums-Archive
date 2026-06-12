---
title: "Incorrect wide screen resolution."
date: 2005-10-22
forum: Desktop Environments
---

### Post by sjlauritsen on 2005-10-22
Greetings fellow Ubuntu users! :)

After upgrading my Hoary to Breezy, my Xorg suddenly won't display the correct resolution!

I used to have 1280x800 but now it will only allow 1280x768. 

My computer is a Fujitsu Siemens AMILO M1425. With a ATI Radeon 9700 Mobility. I'm using the "fglrx" driver.

Things like Warcraft 3 works perfectly with Cedega, and nothing else seems to be wrong.

This is my xorg.conf:
[http://www.sjl.dk/download/xorg.conf.txt](http://www.sjl.dk/download/xorg.conf.txt)

This is my Xorg.0.log:
[http://www.sjl.dk/download/Xorg.0.log.txt](http://www.sjl.dk/download/Xorg.0.log.txt)

One thing though, there is a line i the logfile:
(--) fglrx(0): Virtual size is 1280x768 (pitch 1280)
- I think this is where the problem is, but how do I solve it?

I've searched for, and tried numberous of tutorials, but nothing seems to be working. :(

Any help would be nice! :)

Best regards,
Søren

---

### Post by santorini on 2005-10-23
This is part of your xorg.conf:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

From the above, you defined a custom "Modeline" with identifier "1280x800@60", so perhaps you should change "1280x800" to (or just add to the front) "1280x800@60" for every occurence below.

	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		24
		Modes		"1280x800"
		ViewPort	0 0 #initial origin if mode is smaller than desktop 
	EndSubSection

The reason why the resolution reverted to 1280x768 might be because it's the closest standard VESA mode. (1280x800's not a standard mode according to my knowledge)

---

### Post by Shaggy on 2005-10-23
The problem goes away if you install the driver from the ATI website instead of using the default one with Ubuntu.  Unfortunately things like dual monitor/screen support also go away becuase when I tried it fglrxcontrol was removed.

So you could wait for an update if it's not that much of a problem to you running a bit smaller.  Or you could just get the ones from ati.

---

### Post by leech on 2005-10-23
I had this same problem, and it is because the driver that comes with Ubuntu doesn't support that resolution.  (ATI's fault, not Ubuntu's) so you may have to wait for a backport.

Leech

---

### Post by sjlauritsen on 2005-10-23
Finally it works! Thanks for your replies!

I was using the default Breezy fglrx-driver. I got it to work using this how-to:
[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

I don't exactly know what I was doing, except that I've installed som special drivers - or something. If someone would explain it a bit, it would be nice.

Another thing I don't understand:
glxgears does not produce any output. I recall it used to, but now it does not! :confused: 

Best regards
Søren

---


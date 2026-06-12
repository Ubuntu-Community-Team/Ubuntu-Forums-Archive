---
title: "Geforce 9400, can't seem to get 1280x768 resolution,"
date: 2009-05-03
forum: General Help
---

### Post by boyofford on 2009-05-03
Hi, struggling to set max screen resolution.

Got a Nvidia GeForce 9400 GT graphics card connected via vga to hdtv.
Using the Nvidia driver version 180

In Nvidia-settings I only have options for 1380x768, 1152x864 and lesser resolutions.
However my tv can support 1280x768, and using 1152x768 sqwishs the picture(noticeable with films).

Any ideas?

Tried manually editing the xorg.conf to correct resolution, but when logged back in the resolution was only 1024x768!

---

### Post by boyofford on 2009-05-04
sorry to do this but... bump:confused:

---

### Post by boyofford on 2009-05-05
At the  risk of someone telling me off for bumping....bump

---

### Post by DJonsson2008 on 2009-05-05
On my machine I had to set the Virtual line
in the 'Screen' section to the desired
resolution, and the modeline to include
the primary configs so these would stick
on reboot.

Also the GUI's provided by Nvidia don't rewrite
xorg.conf unless you you tell them too and are
running the program as root, so they can be
a bit deceptive in that regard when the resolution
you set does not stick.


Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@76"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

---

### Post by boyofford on 2009-05-13
Almost there! turns out my Vistron 32" has a has max resolution of 1366 x 768 pixels.

By changing the HorizSync to 48-60 and the VertRefresh to 60-75 I was able to get a resolution of 1300 x 768 (or 1320 x 768, can't remember). Got these values from a arch forum ([thread]("http://bbs.archlinux.org/viewtopic.php?id=69654"))

Not quite right, image goes off screen slightly at top but at least its working widescreen.

Tried to install the latest nvidia driver from the nvidia site too, but no joy there.

Can't find what the HorizSync and VertRefresh should be anywhere else.

Anyhow just thought I'd post incase usefull to anyone else.

---

### Post by boyofford on 2009-05-13
Might try envy next, going to have to reinstall my system anyhow becuase XBMC doesn't see any graphics card now!:o

---

### Post by Lyn Grider on 2009-05-15
I'm a new Ubuntu user, and I hope this post is appropriate . . . ;)

This isn't an answer to the question on this thread; it's a slightly different question on the same concept: I'm running Hardy Heron on an old IBM Pentium 4 at 1.80 GHz. I'm using a ViewSonic LCD monitor, and when I start up, I get a message on the screen that advises me to set my screen resolution at 1280 x 768. But when I go to change screen resolution, that setting isn't in the drop-down menu. The finest resolution is 800 x 600 (or the other way round . . . I don't remember for sure). 

There's nothing wrong with the appreance of my display in Ubuntu in that resolution, but
I'm using a Belkin switch to mange two computers on one monitor, and not being able to change the resolution in Ubuntu means I have to change it every time I go to the other computer (which is running Windows . . . :redface:), and having the wrong resolution messes up the icon placement on my desktop. I'm trying to wean myself off Windows by learning the Linux software (OpenOffice, etc.) and switching all my frequently-used data files as I use them, but in the meantime, I'd like to resolve (pun intended) this issue if possible.

Thank you.

---


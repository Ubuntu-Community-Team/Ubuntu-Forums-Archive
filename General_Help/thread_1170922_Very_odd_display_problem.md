---
title: "Very odd display problem"
date: 2009-05-26
forum: General Help
---

### Post by Dr Belka on 2009-05-26
Okay, so I have a very odd problem with ubuntu since I have been using 9.04.  When I boot up and get to the login screen, the screen position is jacked up.  The upper half of the screen is on the bottom and the lower half of the screen is on the top (I cannot think of a good way to describe this).  It remains this way through the login and remains when the desktop starts up.  

As I can find no other solution, I simply turn my monitor (1280x1024) off and turn it back on.  This fixes the "flipped aspect of my problem" but after this is done, the screen is off center and it is about 20 pixels too wide for the screen.  I center it as best as I can using some buttons on the monitor itself, but I am still annoyed by the fact that the "show desktop" button, the ubuntu symbol in the upper right hand corner, and the trash can are covered.  

Also, I have an nVidia GeForce4 MX graphics card and the hardware drivers manager installed the nVidia driver version 96 for me.  I imagine that this has something to do with my problem.  

Any Ideas? Do I need to clarify my problem?

---

### Post by khelben1979 on 2009-05-26
I'm not sure how to fix this problem, but it would be interesting to see how your /etc/X11/xorg.conf looks like.

Please post this to this thread.

---

### Post by redsoxreed on 2009-05-26
Does your monitor have an "Auto Adjust" button or something similar?

---

### Post by Dr Belka on 2009-05-26
> **khelben1979 said:**
> I'm not sure how to fix this problem, but it would be interesting to see how your /etc/X11/xorg.conf looks like.

Please post this to this thread.
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by Dr Belka on 2009-05-26
> **redsoxreed said:**
> Does your monitor have an "Auto Adjust" button or something similar?
Yes, but this doesn't fix anything : (

---

### Post by khelben1979 on 2009-05-26
That xorg.conf file is very short and does not contain all the information which you will get with this new install:

I would recommend that you backup the xorg.conf file and then proceeding over to the nvidia site and download a suitable driver.

```
cd /etc/X11/
sudo cp xorg.conf xorg-old.conf
```

Make sure you kill off the x-server including the GDM process and then log in to a text console. From there you open up the nVidia driver and make sure to use sudo as you need root priviligies, then you go on with the installation.

If you get problems with this in the way that the graphics isn't working, you always have the possibility to go back to your old xorg.conf file by renaming it back to it's original name:

```
cd /etc/X11/
sudo cp xorg-old.conf xorg.conf
```

---


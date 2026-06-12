---
title: "Strange size issues with GDM and Gnome Panel"
date: 2008-08-09
forum: Desktop Environments
---

### Post by jonathanfspencer on 2008-08-09
Hey Everybody,

With my new install of Ubuntu 8.04 64-bit on my notebook, Gnome Panel and GDM seem to not be sized up quite right.  This is a Gateway T-6836 model with an Intel GMA graphics adapter and a 14.1" 1280x800 LCD.  As you can see from the picture, the size of my background image is correct, but I cannot seem to get the Gnome Panel to stretch across the entire top.  Furthermore, when I had a bottom panel, it seemed to float a bit above the bottom left corner and did not take up the entire screen.  GDM does something similar, occupying only the top left section of the screen and showing the Ubuntu orange-brown color for the remaining lower right border.  It's as if GDM and Gnome Panel think my resolution is 1024x768 but X knows that it's 1280x800.  I have tried adding a "Virtual 1280 800" line in the Display subsection in my xorg.conf, but that does not change anything. Any ideas?

Thanks a ton.  Great forum.  Oh, let me know how to do a screenshot of the login screen and I'll post that.

---

### Post by cdtech on 2008-08-09
The virtual setting is for your login screen. You could try to set the default screen size within your "/etc/X11/xorg.conf" file:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900" "1920x1440" "1920x1200" "1856x1392" "1680x1050" "1440x900@60" "1400x1050"  "1280x800@60" "1280x720@50" "1280x720@60" "1280x768@60" "1280x854" "1152x768@54" "1024x768" "800x600@60" "800x600@56" "1440x900" "1920x1440" "1920x1200" "1856x1392" "1680x1050" "1440x900@60" "1400x1050"  "1280x800@60" "1280x720@50" "1280x720@60" "1280x768@60" "1280x854" "1152x768@54" "800x600@60" "800x600@56"
    EndSubSection
EndSection
```
You can see that in the "Modes" part of my configuration the first size is my default size, the rest are just options.

You could also try to set your screen size using:
```
sudo displayconfig-gtk
```

Hope this helps.....

---

### Post by jonathanfspencer on 2008-08-10
Thanks for the suggestions, cdtech.  Unfortunately, I have tried those and am still getting nowhere.  Here's my xorg.conf:
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes	"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

When I run displayconfig-gtk, it shows my resolution as 1024x768 as I suspected, but I cannot set it any higher.  It also shows my refresh rate as 30Hz, but I cannot set it any higher, either.  I tried setting my monitor to be a Generic 1280x800 widescreen LCD panel, but X freaks out when I try to test my configuration (I do not know how to describe this, but I'm sure most seasoned X users have experienced this at some point in the past 10 years - very distorted with what looks to be multiple columns of my screen, each with its own cursor and whatnot).  My video driver is just the VESA one according to displayconfig-GTK, but it's working great with Compiz-Fusion.  When I try to change it to the Intel GMA 965 driver, I get an error message that "Configuration Test Failed: Please verify the selected devices and configuration."

Here's a screenshot I find mildly amusing - displayconfig-gtk showing one thing and Ubuntu's resolution settings showing another.

---

### Post by ilario73 on 2008-08-10
I have exactly the same problem with my 8.04 64-bit installation on a Packard Bell BV EasyNote_BG46-P-050IT.
I also have the same chipset for graphic card: intel 965.

I also tried to follow the suggestions of cdtech but ending up with the same problem described above....

Could be a problem with the chipset??

Thanks for any help,
   Ilario

---

### Post by jonathanfspencer on 2008-08-10
ilario73 and I have pretty similar machines.  Here's a link to the specs on his Packard Bell:
[http://www.packardbell.it/products/notebook/easynote-bg-white/EasyNote+BG46-P-050/productsheet-PC12E04606-1272.html]("http://www.packardbell.it/products/notebook/easynote-bg-white/EasyNote+BG46-P-050/productsheet-PC12E04606-1272.html")
and to my Gateway:
[http://support.gateway.com/s/Mobile/2008/Triton/1015592R/1015592Rsp3.shtml]("http://support.gateway.com/s/Mobile/2008/Triton/1015592R/1015592Rsp3.shtml")

Is anybody else experiencing this?  Has anyone solved it?

---

### Post by Ecologger on 2008-08-17
see [http://ubuntuforums.org/showthread.php?t=881127&highlight=gateway+T-6836]("http://ubuntuforums.org/showthread.php?t=881127&highlight=gateway+T-6836")for a guide on the T-6836. I fixed mine by editing the virtual to 1280 800 AND adding the default 12800x800@60 in the modes. Then restart X server and use display-gtk to change the resolution to 1280X800. You have to reset it every time you restart so i suggest just hibernating it all the time.

---

### Post by ilario73 on 2008-08-26
Thanks Ecologger, the tricks worked, but without having to works with xorg.conf, simply following the indication regarding xinitrc according to the indication gave in the link you cited.
Ilario

---

### Post by jonathanfspencer on 2008-09-22
Hey, it looks as though this is fixed in Intrepid Ibex 8.10.  Awesome!  Now, if I could just figure out why it got rid of my Network Manager...

---


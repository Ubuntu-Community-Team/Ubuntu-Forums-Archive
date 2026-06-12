---
title: "Dual screen window behavior"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by fizban9 on 2008-01-10
Last week I installed Ubuntu Gusty on my computer and I've spent the last week chasing down the solution to one problem after another.  Each one has been like a puzzle and as I've solved them I've learned a lot about how Ubuntu and Linux work.

Now I'm trying to get my display to work right.  I have a dual monitor setup running off of a Nvidia 7900 GT.  The monitors are exactly the same, 19" LCDs running at 1280x1024.  Also, I'm using the Envy drivers for my card.

Initially the two monitors were acting as separate desktops, with the Gnome panels only running along 1 screen and windows maximizing to fill only 1 monitor.

Then I decided I wanted to test out the fancy desktop effects and to do that I had to install xserver-xgl.  Which works, but now I only have 1 desktop that spans both monitors.  More annoying than windows maximizing across two screens is that everything opens right in the divide between the screens.

Here are the relevant entries from my xorg.conf file:

```
Section "Monitor"
	Identifier	"Q9-2 Series"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection


Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Boardname	"nv"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Monitor		"Q9-2 Series"
	Defaultdepth	24
	Option		"UseFBDev"	"true"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection


Section "device" #                                                     
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	1
EndSection


Section "screen" #                                                     
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection


Section "monitor" #                                                     
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection


Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection]
```

I'm not really sure how to read it.  I have two monitor entries, two screen entries and two device entries.  I've read something about setting up twinview but I couldn't figure it out.  I also read that I need to set some sort of "meta mode"???

Any help would be appreciated.  I'm |<------this----->| close to ditching XP forever.

---

### Post by chewearn on 2008-01-10
Did you use nvidia-settings?

Top Menu > Applications > System Tools > Nvidia Settings

---

### Post by fizban9 on 2008-01-10
> **AstalaVista said:**
> Did you use nvidia-settings?

Yes, but it doesn't work because I am using the Envy drivers instead of the Nvidia drivers.  It says:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server

But I can't use the Nvidia drivers because they dont work with xserver-xgl.  I need that to enable the desktop effects.  I tired running the command anyways and it didn't change anything.  Still gives me the same error.

---

### Post by chewearn on 2008-01-11
> **fizban9 said:**
> Yes, but it doesn't work because I am using the Envy drivers instead of the Nvidia drivers.  It says:



But I can't use the Nvidia drivers because they dont work with xserver-xgl.  I need that to enable the desktop effects.  I tired running the command anyways and it didn't change anything.  Still gives me the same error.

I can't remember the exact steps; but:
1. nvidia driver thru Envy,
2. plus getting recognized by Restricted Driver Manager,
3. so that you can run nvidia-settings,
4. and enable full desktop effects, 
5. without xserver-xgl;

is very possible; because I have two computers working in this combination.

After running Envy installer, and install the nvidia drivers; try running restricted driver manager, see if it is possible to "check" enable video driver.

---

### Post by EXCiD3 on 2008-01-11
Xinerama is meant for the desktop spanning both monitors if im not mistaken. Shouldnt this be set to false in the xorg? Also which video driver are you using?

---

### Post by fizban9 on 2008-01-11
> **EXCiD3 said:**
> Xinerama is meant for the desktop spanning both monitors if im not mistaken. Shouldnt this be set to false in the xorg? Also which video driver are you using?

I tried disabling xinerma, my nifty dekstop effects stayed on and technically the second monitor worked but it was just blank and I couldn't no anything with it, so I turned Xinerma back on.

Also, I'm using the Envy Nvidia drivers.

---

### Post by EXCiD3 on 2008-01-11
Open up Nvidia-settings and find out *exactly* what the nvidia driver version you are using. Probably if you are using the most recent envy, then you probably will have the most up-to-date nvidia driver also (169.07 according to the nvidia website: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html))

---

### Post by chewearn on 2008-01-12
> **fizban9 said:**
> I tried disabling xinerma, my nifty dekstop effects stayed on and technically the second monitor worked but it was just blank and I couldn't no anything with it, so I turned Xinerma back on.

Instead of using Xinerama, I have always had better results with Twinview or Separate X screens.

I suggest turn off Xinerama, then use nvidia-settings to turn on either Twinview, or separate x screens (see which one you prefer).

---

### Post by fizban9 on 2008-01-14
> **AstalaVista said:**
> Instead of using Xinerama, I have always had better results with Twinview or Separate X screens.

I suggest turn off Xinerama, then use nvidia-settings to turn on either Twinview, or separate x screens (see which one you prefer).

Wow!  I can't believe it ended up being that easy.  I had to uninstall xserver-xgl first, then enable twin view from the Nividia serttings thing.  

Thanks alot for the help!

---


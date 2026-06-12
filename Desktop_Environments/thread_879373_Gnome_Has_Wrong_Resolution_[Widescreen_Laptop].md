---
title: "Gnome Has Wrong Resolution [Widescreen Laptop]"
date: 2008-08-03
forum: Desktop Environments
---

### Post by kaoskorruption on 2008-08-03
I recently got a Gateway T-6836 laptop and installed Ubuntu. Everything worked except that Gnome doesn't seem to realize that it is a widescreen. Look:

[[IMG]http://img378.imageshack.us/img378/7975/desktopka7.th.png[/IMG]](http://img378.imageshack.us/my.php?image=desktopka7.png)

[[IMG]http://img47.imageshack.us/img47/4277/screenshoteh4.th.png[/IMG]](http://img47.imageshack.us/my.php?image=screenshoteh4.png)

-Checking the "clone screens" option causes it to fill up the entire screen, but it also stretches the picture out rather than making it widescreen.

-I have no idea why there is an "unknown" screen there. It's a 14" screen and nothing else.

-In the "Screen Graphics And Preferences" (sudo displayconfig-gtk) if I check the widescreen option it simply doesn't stay. Changing much of anything with this tool just reverts back to what it was originally (see picture).

If it would help I can upload my xorg.conf. Thanks so much to anybody that can offer help.

---

### Post by K2712 on 2008-08-03
Actually, could you post the output of:

```
xrandr
```

And it couldn't hurt to attach your xorg.conf, either...:)

---

### Post by zxscooby on 2008-08-03
what kind of gfx card do you have?

---

### Post by kaoskorruption on 2008-08-04
Graphics card is Intel Media Accelerator X3100.

Here is the result of xrandr:
```
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 768
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x768       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       30.0* 
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  

```

Here is my xorg.conf:

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
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	768
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by K2712 on 2008-08-04
Try:

```
xrandr --output TV --off
```

---

### Post by kaoskorruption on 2008-08-04
[COLOR="Blue"][SIZE="7"]THANK YOU[/SIZE][/COLOR]

It worked! That wasn't that hard, but it certainly would not be something that I would have known to do.

So what exactly, in technical terms, did that do?

---

### Post by K2712 on 2008-08-04
You're very welcome. :)  It seems that your xorg.conf was configured with your normal screen, and a "ghost" screen, in this case the TV output which is probably the VGA out on your laptop.  The ghost screen's resolution was being used by the Xserver for your main screen, which was obviously undesirable.

To make this change permanent you should add the following line to the "Monitor" section in your xorg.conf:

Option "Ignore" "true"


For more info on xrandr see here:

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by kaoskorruption on 2008-08-04
Okay, adding that line to the xorg.conf indeed made it permanent - though one small issue: it works only once I login. The login screen is still holding the "ghost screen" resolution.

---

### Post by K2712 on 2008-08-04
That is usually caused by an incorrect 'Virtual' line in the Screen section of xorg.conf.  In your case though the Virtual resolution seems to be correct.  If the resolution is off all the way from boot to desktop, you may want to try the following suggestion in this post from dreadlord_chris:

[http://ubuntuforums.org/showthread.php?t=383492](http://ubuntuforums.org/showthread.php?t=383492)

---

### Post by kaoskorruption on 2008-08-04
The thing about that is that the Ubuntu splash screen (usplash) when it boots up is not in the wrong resolution. Everything looks right when it boots up and after the login screen. It is only the login screen at this point.

I also started to add the vga option as your last post suggested and my menu.list doesn't even have the vga option in it, so I decided I'd just add it to the end of the line. But when I googled around for some widescreen VGA codes I was unable to find any anyways so it didn't really matter.

Anyways, really appreciate your help still, though I'm stuck again :(

---

### Post by K2712 on 2008-08-04
I'm almost out of ideas, maybe try to just comment out that Virtual line, because I think that gdm looks to the first resolution in your Screen section, which in this case is the same as the Virtual setting, so it is unnecessary.

---

### Post by kaoskorruption on 2008-08-04
Okay haha I just had an idea. More of me realizing what the problem is. The login screen seems to be getting its resolution from the other "ghost screen" rather than the login screen, and it's resolution seems to be at 800x600. I just need to figure out how to make the login screen use the same screen section in the xorg.conf as when I login.

Update... nope that can't be it. I just deleted all other screen and monitor sections other than the main ones that it actually uses and that changed nothing. Here is my xorg.conf as of right now:

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
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Virtual "1280x768"
		Depth	24
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by K2712 on 2008-08-04
The format of the Virtual line should be:

Virtual 1280 768

but I still don't think you need it.

Have you ever tried to run:

```
sudo dpkg-reconfigure xserver-xorg
```

You should probably make a backup of your current xorg.conf to keep as a reference.

---

### Post by kaoskorruption on 2008-08-04
Okay, tried that, no success. Nothing changed. What is really weird to me is that when I did that, it indeed changed my xorg.conf, but yet when I logged in the screen was perfectly fine. I did not have to go and add that line into my xorg.conf that you originially told me to add to fix the first problem.

This makes me wonder (1) if xorg.conf is being used and (2) if there is some other configuration file being used here.

---

### Post by K2712 on 2008-08-04
Hmmm, that is strange, but I can tell you that your xorg.conf is definitely being used, but it looks like there are still some things I don't know about X11.  Sorry doesn't look like I can be of any further help...

---

### Post by kaoskorruption on 2008-08-05
That's alright, I really appreciate how much help you've given already. You helped me fix the big problem which is once I login. I'll pass this on to others with the same laptop that have the problem.

---

### Post by mangy_mathan on 2008-08-05
I had a similar problem. My computer kept ignoring all my attempts to turn it to 1280X800.

It turned out that the intel driver that came preinstalled, the i810 one, had a bit of a problem rendering that resolution.

Instead I installed the intel driver using

```
sudo aptitude install xserver-xorg-video-intel
```

and it worked. You may still have to run your configuration with

```
sudo dpkg-reconfigure xserver-xorg
```

Hope that helps somewhat.

---

### Post by kaoskorruption on 2008-08-05
Apparently it's already installed.

---


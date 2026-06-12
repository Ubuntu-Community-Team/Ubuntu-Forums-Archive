---
title: "URGENT! new LCD screen problems"
date: 2009-03-14
forum: General Help
---

### Post by windows-killer on 2009-03-14
I just bought a new monitor **Viewsonic Optiquest Q19wb**
I plunged it in and it worked, but I started changing the resolution and suddenly the monitor blanked out and I got an error message saying Out of frequency, I restarted X server and it turned back on, but as soon as I log on it turns black again.

here is what I tried to fix the problem:
I pressed CTRL+ALT+F1 to go to the command line session and I typed 

```
sudo dpkg-reconfigure xserver-xorg
```
I answer all the questions but its still not working, then I tried

```
sudo X-configure
```
But then I get the command not found error

next I tried ```
xrandr -s1024x768
```this worked once but I messed up again by adjusting the resolution:x I put the same command many times but its not working

finally I tried ```
sudo nano /etc/x11/xorg.conf
``` it brings me to a screen with shortcut keys but am unable to use them, but if I press F3 to write to the file it says file not found:S

I have a 128 MB ATI 92500 video card if that helps at all

is there a screen like the one in recovery mode that provides me the option to chose my resolution?
someone please help me, I have been very frustrated working this out.:S

EDIT: I am getting the command not found message when I put this command as well ```
sudo dpkg-reconfigure x
```

---

### Post by kestrel1 on 2009-03-14
I would suggest that you remove your xorg.conf file & a new one will be made when you reboot: ```
sudo rm /etc/X11/xorg.conf
```
Ensure that the X in X11 is a capital X.

---

### Post by windows-killer on 2009-03-14
> **kestrel1 said:**
> I would suggest that you remove your xorg.conf file & a new one will be made when you reboot: ```
sudo rm /etc/X11/xorg.conf
```
Ensure that the X in X11 is a capital X.

with the command above ubuntu keeps on booting into safe graphics mode, I cant get it to start in normal mode.
I did load a new profile but it shows some lines on the screen and am unable to see anything.


I never knew this would be that hard!:(

---

### Post by kestrel1 on 2009-03-14
Did you try running```
sudo dpkg-reconfigure xserver-xorg
``` after the above command?
It should work.

---

### Post by ajgreeny on 2009-03-14
I think ```
sudo dpkg-reconfigure xserver-xorg
``` is deprecated in newer versions of ubuntu (since hardy?) and is a waste of time.  I suggest you reboot into recovery mode and run *xfix* when you get to that menu.  It should detect your hardware again, as it does at installation, and give you a better start, even if you need to reset the resolution to what you want.

Incidentally, you can edit the xorg.conf file and it will be used, even though it is nearly empty by default.  I had to do this for mine in intrepid to get a decent scroll in firefox and to get the resolution I wanted.  Here's the meat of mine as an example, with my desired resolutions spelled out:-

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    
    Option "AccelMethod" "EXA" #This line added to speed up scrolling in some applications.
    Option "MigrationHeuristic" "greedy" #This line added to speed up scrolling in some applications.
    EndSubSection
EndSection
```

---

### Post by kestrel1 on 2009-03-14
Forgot about 'xfix'
Thanks for pointing that out.

---

### Post by blackened on 2009-03-14
> **ajgreeny said:**
> I think ```
sudo dpkg-reconfigure xserver-xorg
``` is deprecated in newer versions of ubuntu (since hardy?) and is a waste of time.

Every time a thread like this comes up someone insists on suggesting this method. I guess the devs didn't shout it loudly enough when they changed away from it, though you'd think a year would be enough time to get it out of our collective system.

Here is a handy link for fixing problems with X: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by windows-killer on 2009-03-14
> **ajgreeny said:**
> I think ```
sudo dpkg-reconfigure xserver-xorg
``` is deprecated in newer versions of ubuntu (since hardy?) and is a waste of time.  I suggest you reboot into recovery mode and run *xfix* when you get to that menu.  It should detect your hardware again, as it does at installation, and give you a better start, even if you need to reset the resolution to what you want.

Incidentally, you can edit the xorg.conf file and it will be used, even though it is nearly empty by default.  I had to do this for mine in intrepid to get a decent scroll in firefox and to get the resolution I wanted.  Here's the meat of mine as an example, with my desired resolutions spelled out:-

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    
    Option "AccelMethod" "EXA" #This line added to speed up scrolling in some applications.
    Option "MigrationHeuristic" "greedy" #This line added to speed up scrolling in some applications.
    EndSubSection
EndSection
```

how do I copy and paste the file on low graphics mode?

---

### Post by windows-killer on 2009-03-14
> **kestrel1 said:**
> Did you try running```
sudo dpkg-reconfigure xserver-xorg
``` after the above command?
It should work.

I tried that I answer all the questions but it doesint fix my problem

---

### Post by kestrel1 on 2009-03-14
If you use the LIVE CD it may be easier.

---

### Post by windows-killer on 2009-03-14
> **kestrel1 said:**
> Forgot about 'xfix'
Thanks for pointing that out.

X fix is the one in recovery mode right?
that was the first thing I tried when the problem occurred but no luck:(

---

### Post by windows-killer on 2009-03-14
> **kestrel1 said:**
> If you use the LIVE CD it may be easier.

can you list some instructions please?

---

### Post by kestrel1 on 2009-03-14
If you use the LIVE CD you can edit the xorg.conf file & you shouldn't be in low res mode.
If you want to edit the xorg.conf file I would do the following:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
That should backup your current file.
You could just copy the above from windows-killer's post & make a new text file & save it as xorg.conf. If you save it to the Desktop do the following:```
sudo rm /etc/X11/xorg.conf
```
```
cd Desktop
```
```
sudo cp xorg.conf /etc/X11/
```
Reboot.

---

### Post by windows-killer on 2009-03-14
> **kestrel1 said:**
> If you use the LIVE CD you can edit the xorg.conf file & you shouldn't be in low res mode.
If you want to edit the xorg.conf file I would do the following:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
That should backup your current file.
You could just copy the above from windows-killer's post & make a new text file & save it as xorg.conf. If you save it to the Desktop do the following:```
sudo rm /etc/X11/xorg.conf
```
```
cd Desktop
```
```
sudo cp xorg.conf /etc/X11/
```
Reboot.

these steps look very hard, is there an easier way to do this? something like the recovery mode that provides me the resolution I want?

It shouldn't be that hard to change the resolution:D

---

### Post by kestrel1 on 2009-03-14
They are not hard. a simple copy & paste in the terminal.
If you use the live CD it will be a different process however.
Use gedit to copy the xorg.conf part of windows-killer's post & save it as xorg.conf on to the Desktop.

---

### Post by windows-killer on 2009-03-14
its almost working but i see so many lines on the screen that am unable to see menus etc

---

### Post by kestrel1 on 2009-03-15
If you have the xorg.conf file as above reduce the screen res by changing this line```
SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```
I would suggest that you change the first mode to 1024x768 to start off with. So the line would read like this:```
SubSection "Display"
        Modes        "1024x768" "1280x1024" "1280x960" "1152x864"  "832x624" "800x600" "720x400" "640x480"
```

---

### Post by kestrel1 on 2009-03-15
You could always use this xorg.conf:```
# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual 1280 1024	Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Acer"
	Modelname	"Acer X193W"
	Horizsync	30.0-81.0
	Vertrefresh	55.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```
Has always worked well on my system. This is for an NVidia graphics card & an Acer 17" TFT screen.

You would want to remove the NVidia section.

---

### Post by windows-killer on 2009-03-15
problem solved! 
I solved this problem by booting to the live CD and recorded some keyboard keys, here's what I did:

boot to ubuntu live CD, with my mouse I pressed applications menu>> pressed the RIGHT arrow key twice on the keyboard to go to system>> then I pressed the DOWN arrow key once to go to preferences >> next I pressed the RIGHT key once to scroll to the about me section, I pressed the "S" key 6 times to go to SCREEN RESOLUTION, pressed TAB once then it brought me to select a resolution, I pressed the DOWN arrow key twice/ or three times, next I pressed ENTER then pressed the TAB key 6 times then ENTER and voila!!! I got my monitor working again. 

I applied the same steps on my ubuntu installation while my screen was black and now its working well!!!

I think its a good tutorial for newbies who avoid the command line.

---

### Post by kestrel1 on 2009-03-15
A different way to do it, but well done :D

---

### Post by windows-killer on 2009-03-16
> **kestrel1 said:**
> A different way to do it, but well done :D

I wish there was an equivalent of every single command in Linux, especially for repair :popcorn::D

---


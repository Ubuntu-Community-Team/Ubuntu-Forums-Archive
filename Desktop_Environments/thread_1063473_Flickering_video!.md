---
title: "Flickering video!"
date: 2009-02-07
forum: Desktop Environments
---

### Post by Travis38 on 2009-02-07
Hi, I recently installed ubuntu and I love it, except one thing. When I play a video in vlc, totem, mplayer, etc., it flcikers, like the video disappears for a second then back, not long enough to make the video hang, but long enough to be very annoying.

---

### Post by Yashiro on 2009-02-08
It's a problem with 'desktop effects'. Set desktop effects to none and the flickering will cease.

---

### Post by warp99 on 2009-02-08
You can change the video driver in mplayer from xv to opengl if you have desktop effects enabled. With Totem you have to manually edit the config file and change the driver. With VLC depending on what version your have using the opengl driver may cause VLC to crash. 

You could also use the X11 video driver if you wanted for the media players, but the video quality will be reduced. In really depends on you graphics card and what version drivers you have installed.

---

### Post by Travis38 on 2009-02-08
How do you set the desktop effects to none? 
In mplayer when I change it to opengl it seems to have no effect on the flickering.
I've got an ATI Hd2600xt, set up with the drivers from envy, so the card and drivers should be good enough.

---

### Post by warp99 on 2009-02-08
If your using the fglrx drivers you can set overlay to on which should help with some of the flickering. You can use the ATI Control panel or add the line manually to your xorg.conf like this:

```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to the following section:
```
Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

```
And add the following lines in bold:
```
Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
[b]	Option	    "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"[/b]
EndSection

```

This should help with the flickering if not eliminate it completely.

---

### Post by Travis38 on 2009-02-08
OH MY GOSH! You are a life saver! Thank you so much! That just fixed the flickering problem! Thank you so much!

---

### Post by warp99 on 2009-02-08
Thanks. One more thing, just mark the thread "solved" so everyone else can see the solution.

---

### Post by JordanL on 2009-02-10
Ok I have the same problem, get the video flickering with desktop effects on. So I goto the console to try the xorg.conf fix, and my xorg file is empty. Actually it doesn't even exist. I have the official ati drivers installed (they work perfectly and they are the only way I could get 3d acceleration and desktop effects to work properly). Did the xorg.conf file move with these ati drivers installed? I dont see any options in the ati control panel regarding opengl/video overlay or the such.

UDPATE: Nevermind I'm just a retard and cant type capital letters into my console lol. X11 not x11. duh

---

### Post by JordanL on 2009-02-10
I still get flickering with desktop effects on. I'm using mplayer with video device set to gl x11 (openGL) with doublebuffering on, direct rendering on and frame dropping enabled.

Also here is my xorg.conf file


```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```
Any suggestions? (and yes I tried restarting x-server (and my whole computer) after saving these changes)

---

### Post by warp99 on 2009-02-10
Your problem may be here:

[i]Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection[/i]

You have two screen sections. Are you running dual monitors? If not I would do the following:

Boot to recovery mode and use the 'xfix' command in the menu list. That will generate a fresh xorg.conf and backup your old one. Once that's done before you boot into multi user mode edit the new xorg.conf using vi or nano:

```
nano /etc/X11/xorg.conf
```

Scroll down to the following section:
```
Section "Device"
	Identifier  "Configured Video Device"
EndSection
```

And add the following lines in bold:
```
Section "Device"
	Identifier  "Configured Video Device"
	[b]Driver      "fglrx"
	Option      "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"[/b]
EndSection
```

With the current version of Ubuntu you don't really need an xorg.conf since RandR is used for most of the video settings, but with the proprietary drivers you sometimes need an xorg.conf to add an option or two.

---

### Post by JordanL on 2009-02-10
Still no good. In fact reseting my xorg file like that just broke it and xserver failed to start. I ran aticonfig --initial again to rewrite my xorg.conf file to one that works with the fglrx driver. It seems as if the driver is not taking any notice to the VideoOverlay or OpenGLoverlay options in the xorg.conf file.

if i go like this (as the aticonfig help says)
```
aticonfig --overlay-type="Xv"
```
it adds those Options to the xorg.conf file but it says this in return

```
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.

```
Does this mean its not using those settings, or that maybe overlay in general is disabled?

---

### Post by JordanL on 2009-02-10
I'm about to give up for now and just disable desktop effects when I want to watch a movie. Maybe the release of xserver 1.6 will fix up a few things.

---


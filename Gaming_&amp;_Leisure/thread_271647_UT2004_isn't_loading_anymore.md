---
title: "UT2004 isn't loading anymore"
date: 2006-10-05
forum: Gaming &amp; Leisure
---

### Post by ekuliak on 2006-10-05
I wanted to play a bit of UT2004 today, so I clicked my shortcut, it loaded the splash screen, but the game never loaded.

So I decided to try it from the terminal and got this:

```

WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: No video mode large enough for 1280x1024


History:

Exiting due to error

```

I don't know what to do about it, and I'm not positive about what broke it.

It could be because I bought a new monitor recently (19" widescreen 1440x900), but I'm pretty sure I was able to get UT2004 running on it though (I know games were the first things I tried when I got it).

I thought maybe editing an ini file might help... but I can't seem to remember where/what it is.

---

### Post by Perfect Storm on 2006-10-05
You might want to reconfigure your xorg file to fit your new screen and with new resolutions.

---

### Post by ekuliak on 2006-10-05
I'm not totally sure I understand what you are saying.  I have already edited xorg so that my resolution of 1440x900 works, is that what you meant?

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA GeForce 6800 GS"
	Monitor		"DELL P780"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I'm also not sure if I should be concerned with this:
```

Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
EndSection
```

That was for my old monitor.  My new monitor is a ViewSonic (VA1912wb).

Hmmmm... Looks like it was in the first code I posted as well.

I wonder if it should be changed to "VIEWSONIC VA1912WB" or something

---

### Post by Perfect Storm on 2006-10-05
Try with
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

remember to backup xorg.conf first

restart X

---

### Post by ekuliak on 2006-10-06
I did that and it didn't seem to help.  I did notice that it changed my monitor to something like "Generic Monitor."  I wasn't able to get my resolution 1440x900 to work either, so I just restored my old xorg.conf file.


I wonder if there is some way to make UT in 1024x768 before loading the game.  I wouldn't mind playing in that mode, since my native resolution probably isn't supported, and 1280x1024 was my old monitor's resolution.

---

### Post by Perfect Storm on 2006-10-07
Okay, try this:

```
cd /home/<username>/.ut2004/System
gedit UT2004.ini

```

Look for **[SDLDrv.SDLClient]**
and change the
WindowedViewportX=640
WindowedViewportY=480
FullscreenViewportX=1600
FullscreenViewportY=1200

to your likenings.

---

### Post by ekuliak on 2006-10-07
That's the ini I was looking for.  I thought I was going crazy because I couldn't find it in the non-hidden System folder.  ](*,) 

Thanks a lot for sticking with me to fix this. =D>

---

### Post by Perfect Storm on 2006-10-07
My pleasure ^_^

---

### Post by scarboni on 2008-08-01
Same error but I don't have an UT2004.ini in my $HOME/ut2004/ directory.

Can't seem to find anyone else with it missing.

Anyway I could never get it to mix sound properly so I'm going to install it into WINE instead see if that gets rid of all the problems.

---

### Post by Brebs on 2008-08-02
The file is ~/.ut2004/System/UT2004.ini

Yes, that's a **dot** ;)

UT2004 uses [OpenAL for sound](http://forums.gentoo.org/viewtopic-t-607847.html).

---


---
title: "Starcraft, resolution weirdness..."
date: 2005-04-18
forum: Gaming &amp; Leisure
---

### Post by Dracontopes on 2005-04-18
When I run StarCraft it runs okay, except for the fact that the screen resolution is weird. When I move my mouse to the borders of the screen, I can scroll into blackness... It's like a virtual desktop (well that's what it is) But Virtual Desktop is disabled in my xorg.conf... 

Running 2.6.11 with Ati 9700pro... XrandR is enabled, I can change resolution on the fly in Gnome. BUT: doing CTRL ALT + or - will NOT change resolution, this will only display again the virtual desktop which I don't want. Anyone know the solution to this?

```

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
	Identifier  "Screen0"
	Device	  "ATI Graphics Adapter"
	Monitor	 "Monitor0"
	DefaultDepth 24
	#Option "backingstore"

	Subsection "Display"
		Depth	   24
		Modes	   "1280x1024" "1024x768" "800x600" "640x480"
		ViewPort	0 0 # initial origin if mode is smaller than desktop
#		Virtual	 1280 1024
	EndSubsection
EndSection

```

---

### Post by manny on 2005-04-19
hmm.. this happened to me in fedora core using wine and the only solution was to have another xconfig with only 640x480 (not 100% sure, use the one and only res that is available on starcraft, i think thats 640x480, cant remember now) Well, make sure you have only that one enabled on xorg.conf. Before playing you'd have to: sudo cp /etc/x11/starcraftonlyres.conf xorg.conf and after playing sudo cp /etc/x11/xorg.conf_backup xorg.conf (Remember to make a backup of xorg.conf before) I guess it's better to log out and then startx an x terminal to play.
Hope it helps (and works) let us know pls.

---

### Post by Dracontopes on 2005-04-19
Having two xorg.conf files just to play a game is a little bit too complicated don't you think :-) There must be another way!

---

### Post by Happy on 2005-04-20
Ripped from the winehq application database fallout section but I believe it applies here as well.

[http://appdb.winehq.org/appview.php?versionId=43](http://appdb.winehq.org/appview.php?versionId=43)

> This is a re-post of a comment I made some time ago, retrieved from google's cache:

I had the same problem, no keyboard in Fallout 1. I found a post on the gentoo.org forums that worked for me. I apologize, I can't seem to find the original post (So credit goes to whomever originally posted this), but basically, I created a shell script:

Code:

#!/bin/bash

cd ~/.wine/fake_windows/Program\ Files/Interplay/Fallout xinit /usr/bin/wine falloutw.exe -- :1 vt10 -xf86config XF86Config-fallout


The XF86Config-fallout file is in /etc/X11/, and the only difference from my normal XF86Config is that I set it so that my only display settings are: 16bpp 640 x 480. The original poster also setup custom modelines for his monitor, but I didn't and everything seems to work fine.

The original poster indicated that this worked for Fallout2 and Warcraft2 as well.

My system is AMD Duron 900, GF4 MX 440, and Gentoo 1.4 release.

-- Aaron

From my understanding you would need to type
sudo xinit /usr/bin/wine fallout2.exe -- :1 vt10 -config ./Xorg.conf-fallout (assuming you are in the same directory as fallout2 and it's associated config file)
to play fallout2 (substitute for starcraft) however when I do this I get the following error:

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

I do not know what the --:1 is supposed to do but vt10 specifies the 10th device number to use?


 > 
vtXX    XX specifies the Virtual Terminal device number which Xorg will
               use.   Without  this option, Xorg will pick the first available
               Virtual Terminal that it can locate.  This option applies  only
               to  platforms such as Linux, BSD, SVR3 and SVR4, that have vir&#8208;
               tual terminal support.


I also do not like having to run xinit and wine as root in order to play a game.

---

### Post by Dracontopes on 2005-04-20
Thank for the possible solution, but I fixed this problem with something else... It's actually really stupid not having found this option earlier :P

Check this out:

In cedega config file:
```

; Use XRandR extension if present
"UseXRandR" = "Y

```

This default value was N. Changing this to Y did the trick :)

---

### Post by Happy on 2005-04-21
[QUOTE=Dracontopes]Thank for the possible solution, but I fixed this problem with something else... It's actually really stupid not having found this option earlier :P

Check this out:

In cedega config file:
```

; Use XRandR extension if present
"UseXRandR" = "Y

```

This default value was N. Changing this to Y did the trick :)[/QUOTE]
This worked for me running standard wine as well!
fallout 2 loaded, the movies played, it was a bit sluggish and took a few minutes to load the screen once I had selected a character (fade-ins were really slow)
but I don't care it worked =)

---


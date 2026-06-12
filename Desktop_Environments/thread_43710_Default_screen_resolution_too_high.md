---
title: "Default screen resolution too high"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Noddy on 2005-06-22
I think this is a general X question but I can't find the answer...

X always starts at the maximum supported resolution. Changing to a mode lower than the maximum e.g. 1024x768 versus a max of 1280x1024 works OK during the session but checking the box "Make default for this computer.." doesn't stick - it always reverts to 1280x1024 after a restart.

Editing xorg.conf and removing the 1280x1024 mode for 24 bit depth half solves this but then I lose the 1280x1024 option all together.

I want the machine to (re)start at 1024x768 (for VNC purposes) but I'd like to keep the option of increasing to the higher res if I'm actually in front of it.

---

### Post by metasyntax on 2005-06-22
in the /etc/X11/xorg.conf on the line that lists resolutions you will have something like:

Modes "1280x1024" "1024x768" "800x600" "640x480"

The order of the list determins which is the default mode, in this case "1280x1024"

if you want "1024x768" to come up first you should be able to put it first:

Modes "1024x768" "128x1024" "800x600" "640x480"

this *should* make 1024x768 the default mode... miond you, I haven done this sine the XFree 3.3 days so YMMV and all that :)

HTH,
meta

---

### Post by Noddy on 2005-06-23
That's what I thought. It doesn't work tho...

With the initial modes:

```
"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350" "1x1"
```the system starts at 1280x1024

More info: Modes "720x400" "640x350" and "1x1" are not actually ever available while additional modes of "1280x960" "1280x800" "1280x768" and "1152x768" are available - clearly not all the Gnome settings are derived from the modes line in xorg.conf.

If I simply remove "1280x1024" only the following four modes are available:

*"1024x768" "832x624" "800x600" "640x480"*

But at least the system starts at 1024x768.
If I put "1280x1024" back in, in the sequence:

```
"1024x768" "1280x1024" "832x624" "800x600" "720x400" "640x480" "640x350" "1x1"
```then I get weirdness - a 1280x1024 screen on a 1024x768 display i.e. the screen is too big for the monitor.

More info: Modes "1024x768" "1280x1024" "832x624" "800x600" "640x480" "1280x960" "1280x800" "1280x768" and "1152x768 are available.

---

### Post by John O'Connor on 2005-06-23
I had same problem and used the following solution:
 1. Copy and paste screen section in xorg.conf
 2. In the new screen section specify a new Identifier and remove the highest resolution setting from the "Modes" lines.
 3 Copy your ServerLayout section, paste it and change the "Identifier" and "Screen" values. 
 4. Comment the original ServerLayout section, you can always restore it later.

After following foregoing steps, you will have 2 Screen sections with different identifiers. You will also have 2 ServerLayout sections, one of which will be commented.

I found this reference which explains the above:
[http://www.x.org/X11R6.8.2/doc/DESIGN2.html](http://www.x.org/X11R6.8.2/doc/DESIGN2.html)

Just to summarise the foregoing, the following are the relevant sections from my xorg.conf file:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34GL [Quadro FX 500]"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Preferred Screen"
        Device          "NVIDIA Corporation NV34GL [Quadro FX 500]"
        Monitor         "DELL E173FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes            "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes            "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "ServerLayout"
#        Identifier      "Preferred Layout"
#        Screen          "Preferred Screen"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
#EndSection

---

### Post by Noddy on 2005-06-23
I've played around with this but it's still not doing what I want.

Are we talking about achieving the same thing? i.e. the computer boots to login 1024x768 but you can switch up to 1280x1024 during a session?

Unless I'm missing something, your method seems to amount to simply removing the highest resolution from the modes* lines (is there a mistake in your post? - the Preferred Layout is commented out).

* The releveant one for both login and session is 24 depth.

I've since discovered that I *can * change the resolution of a Gnome session by NOT checking "Make default for this computer.." but checking Save current setup at logout. Gnome must remember this in one of its own configuration files because xorg.conf is not altered by this (Gnome also offers modes not listed in xorg.conf). However, the highest available mode is capped by what is listed in the modes lines of xorg.conf.

The problem is that X always starts at the resolution listed first in the modes lines whereas the screen always starts at the highest resolution listed in the modes lines.

---

### Post by BuhSnarf on 2005-06-23
[QUOTE=Noddy]I think this is a general X question but I can't find the answer...
[/QUOTE]

You can also run:

sudo dpkg-reconfigure xserver-xorg

And it will take you through step by step and you can just unselect the resolutions you don't want.

Is a bit of a long way round for something that should be in a control panel.

---

### Post by Noddy on 2005-06-25
The thing is, BuhSnarf, I want all the resolutions. I simply want to start at less than the maximum resolution. I want the login page to come up at 1024x768 but I'd like 1280x1024 and 1280x960 available in the user sessions.

Seems impossible.

---

### Post by filemanager on 2005-07-02
[QUOTE=BuhSnarf]You can also run:

sudo dpkg-reconfigure xserver-xorg

And it will take you through step by step and you can just unselect the resolutions you don't want.

Is a bit of a long way round for something that should be in a control panel.[/QUOTE]


I did that (because I'm very new to Linux and it was the easiest to do I think. The xconf file was "read only" bah), and it worked perfectly! Thanks! 8)

---


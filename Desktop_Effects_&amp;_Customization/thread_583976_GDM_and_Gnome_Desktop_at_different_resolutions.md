---
title: "GDM and Gnome Desktop at different resolutions"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by feeman_4_life on 2007-10-20
My screen resolution is set at 1680 x 1050 @ 57hz using a LG wt 204 monitor.

My GDM is always slightly off, I suspect it is using the same resolution, but always at a different refresh rate.  The GDM and gnome desktop doesn't match up perfectly.  Is there a way to resolve this?

Also when I watch videos on totem, and I change it to full screen, it changes my entire desktop resolution 1680 x 1050 @ 50hz. At this res, it looks exactly like my gdm screen, and I always have to manually change it back.  Is there a way to fix this as well?

Thank you for any help in advance. =)

---

### Post by Malcolm on 2007-10-21
I'm experiencing the same problem.

My screen's resolution is 1280x1024 at 75Hz but in GDM and whenever I watch a movie in full screen mode I get the same resolution but at 60Hz, resulting in a distorted image shifted to the left.

---

### Post by Malcolm on 2007-10-29
I backed up my xorg.conf and tried to reconfigure the display with:

sudo dpkg-reconfigure xserver-xorg

and when I came to the dialog that would let me select the best resolution/refresh rate to use (I chose the "medium" option), for most resolutions there were several refresh rates to choose from, but for 1280x1024 I could only choose 60 Hz, no way to get it at 75 Hz.

After this, I had to restore my previous xorg.conf, because then even Gnome would only have the 60 Hz setting available.

Is there any way to manually set it to 75Hz?

---

### Post by Malcolm on 2007-10-30
Hello,

so this is how I solved it. I used this online video timing calculator:

[http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html)

I gave it the setting I wanted, 1280x1024@75Hz, and following the four steps it generated the modeline for my xorg.conf. It is important to note that that's the only modeline generator that worked for my case.

So I edited my xorg.conf file and under the Monitor section added the modeline, like this:

```
Section "Monitor"
	Identifier	"SyncMaster"
        Modeline "1280x1024@75"   135   1280 1296 1440 1688   1024 1025 1028 1066  +hsync +vsync
	Option		"DPMS"
EndSection
```

I used the "1280x1024@75" identifier because if I used "1280x1024" the problem would persist (I suppose there's another "1280x1024" mode defined somewhere else which has precedence on my own).

Next I modified the screen section so that it would include the correct identifier, like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024@75" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

I restarted X, and the problem was solved - GDM displayed correctly. Going to try movies now. :)

---


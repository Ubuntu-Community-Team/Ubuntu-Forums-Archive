---
title: "widescreen 1920x1200 on optiplex 745"
date: 2007-07-09
forum: Dell  Ubuntu Support
---

### Post by eb207 on 2007-07-09
I'm having widescreen problems on my dell optiplex 745. 


I'm running 64 bit 7.04 on an optiplex 745. The video card is intel GMA3000 and the monitor is  Dell UltraSharp 2407FP,Wide Flat Panel.

The gui screen resolution stuff gives me an option for 1600x1200.

I've seen various posts on this topic, but all are for slightly different combinations of hardware etc. I did try adding 1920x1200 to my xorg.conf and restarting x, but that didn't give me any more choices.

I also tried installing 915resolution package, and that didn't seem to do it either.

here's the screen section of my xorg.conf file. i added 1920x1200 at the bottom...

any suggestions appreciated, thanks.

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82Q963/Q965 Integrated Graphics Controller"
	Monitor		"DELL 2407WFP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by Ex-Cyber on 2007-07-09
Try this instead (make a backup, of course):

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82Q963/Q965 Integrated Graphics Controller"
Monitor "DELL 2407WFP"
DefaultDepth 24
SubSection "Display"
Virtual 1920 1200
Depth 1
Modes "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Virtual 1920 1200
Depth 4
Modes "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Virtual 1920 1200
Depth 8
Modes "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Virtual 1920 1200
Depth 15
Modes "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Virtual 1920 1200
Depth 16
Modes "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Virtual 1920 1200
Depth 24
Modes "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

---

### Post by eb207 on 2007-07-09
thanks for the suggestion. This didn't quite work.

When I did it, I ended up with part of the desktop extending off to the right beyond the screen.  Also the mouse pointing got off, and you had to click to the left of where you intended to select things.

It seems like people solved this for gma915. is my problem that i have gma3000? or is it that i'm using 64 bit somehow?

---

### Post by tonyperez on 2008-03-14
> **eb207 said:**
> thanks for the suggestion. This didn't quite work.

When I did it, I ended up with part of the desktop extending off to the right beyond the screen.  Also the mouse pointing got off, and you had to click to the left of where you intended to select things.

It seems like people solved this for gma915. is my problem that i have gma3000? or is it that i'm using 64 bit somehow?

Try this:

        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1920x1200@60"  "1680x1050@60"  "1600x1024@60" "1440x900@60"    "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"   "800x600@56"
        EndSubSection

---


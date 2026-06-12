---
title: "inspiron 530 resolution"
date: 2008-01-19
forum: Dell  Ubuntu Support
---

### Post by OAP on 2008-01-19
i have new instal of 7.10 and am having a problem setting resolution for my Targa LCD 19" Widescreen at 1440x900@60Hz.
the system has an Intel integrated GMA 3100.
see below

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Integrated Graphics Controller"
	Monitor		"LCD 19-4 Wid"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection

i am concerned about the line:- virtual 1400  1050
and do not wish to add "1440x900@60" until i know what this means
i also have wobbling windows when closing them, any connection?

---

### Post by gbrainin on 2008-01-19
Adding "1440x900@60" to the Modes line should make that resolution available as an option that you can select.  If that's the resolution recommended for your monitor, it should be okay.

I'm not familiar with the "virtual" line (my xorg.conf doesn't have it), but I can only assume it refers to a virtual screen resolution (one that may run off the edges of the physical screen).

I have no idea if this has anything to do with your wobbling problem.

---

### Post by OAP on 2008-01-19
i tried 1440x900@60 and checked widescreen in Screens and Graphics, the display does not fill the screen there is a vertical blank band of about 2" down the left of the screen.the xorg.config now reads;-
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Integrated Graphics Controller"
	Monitor		"LCD 19-4 Wid"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1280x854"	"1280x768@60"	"1152x768@54"	"1280x720@60"	"800x600@60"	"1280x800@75"	"800x600@85"	"1280x768@75"	"800x600@75"	"1280x720@50"	"800x600@72"	"1280x800@60"	"800x600@56"	"1440x900@75"	"720x400@85"	"1440x900@60"	"640x350@85"	"1600x1024@60"	"640x400@85"	"1680x1050@60"
	EndSubSection
note the change in the Virtual line! can anyone explain this?

---


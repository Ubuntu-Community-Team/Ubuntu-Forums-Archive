---
title: "At wit's end with refresh rate.  Help please."
date: 2005-08-17
forum: Desktop Environments
---

### Post by Dolphin on 2005-08-17
I simply cannot figure this out.  My monitor at native res will do 75hz.
In ubuntu, I couldn't change it from 60.  It was a small worry I glanced at once in awhile.  I wanted to get it fixed but it wasn't dire that I do immediately.

Now I've installed the latest ATI drivers and it dropped my refresh to 47!??  What the heck??  I've editted my xorg.conf until I'm blue in the face.  No change I make makes any difference.

Here's the pertinent info in my xorg.conf

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 (R420 JK)"
	Driver		"fglrx"
	Option		"UseInternalAGPGART" "no"
	BusID		"PCI:1:0:0"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-63
	VertRefresh	56-70
	Modeline	"1280x800@70" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 (R420 JK)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

And my monitor specs.

Horizontal Freq - 30-63 kHz
Vertical Freq - 56-75 Hz


Please help me before I pull out my hair.  Thank you.

---

### Post by yeonil on 2005-08-18
I have changed this:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-63
	VertRefresh	56-70
EndSection

```
Into this
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-63
	VertRefresh	56-75
EndSection

```
but i haven't got the modeline part, where there is also an indication, as i see...let's hope that helps, or some smarter person than me will answer this

Yeonil

---

### Post by Dolphin on 2005-08-18
Yeah, I had that set to 70 while I was testing something.  I've since put it back to 75, it wasn't the problem.  Thanks though.

Anyone else?

---

### Post by Dolphin on 2005-08-18
Sorry for the bump, this is still a problem though.

---

### Post by dbott67 on 2005-08-18
Not sure if this will work for you, but it has helped me a number of times in the past few months.  Like you, I was having issues with refresh rates and also modelines and resolution.  I got really lucky one time and happened to find a "needle in a haystack", so to speak, when I found someone's posted Xorg.conf file on another site and it worked for me.   However, I have since found a better trick:

1. Download & burn a copy of the Ubuntu "Live CD" (or kubuntu/knoppix) --- it seems to do a great job of finding the appropriate video settings (not sure why the installed version doesn't work quite the same way).

2. After booting from the live cd, try to adjust your video settings to your preferred refresh & resolution.

3.  If it works, make a copy of the xorg.conf file and copy it to floppy/USB or e-mail it to yourself or print it out...

4. Boot back into your installed version, backup your existing xorg.conf file and then copy the xorg.conf file from the "live session".

5. Restart your x windows session (or re-boot) and you should be able to tweak your video settings to your desired refresh rate.

I've also used kubuntu live cd & knoppix with good results.

Good luck,
Dave

---

### Post by mapman on 2005-08-18
It could also be that your monitor is lying  to x server about it's capabilities.  By default the x server uses the first option below regardless of what you set in the refresh rate in your xorg.conf (from what i gather, correct me if i'm wrong).  
   By setting the 2nd option below to true may correct your problem by forcing the X server to read your refresh rates in xorg.conf(which should match up to your monitor's manual or else you could 'break' your monitor).  You can check if your monitor sends EDIDs by checking the xorg.0.log file (or something like that)  in /var/log (i think that 's where it is) before you try this.  Let me know if this works.  Don't do this if you're unsure.  I tried it and it seemed to work though (so far).

 Option "UseEdidFreqs" "boolean"
                This option causes the X server to use the HorizSync
                and VertRefresh ranges given in a display device's EDID,
                if any.  EDID provided range information will override
                the HorizSync and VertRefresh ranges specified in the
                Monitor section.  If a display device does not provide an
                EDID, or the EDID does not specify an hsync or vrefresh
                range, then the X server will default to the HorizSync
                and VertRefresh ranges specified in the Monitor section.

        Option "IgnoreEDID" "boolean"
                Disable probing of EDID (Extended Display Identification
                Data) from your monitor.  Requested modes are compared
                against values gotten from your monitor EDIDs (if any)
                during mode validation.  Some monitors are known to lie
                about their own capabilities.  Ignoring the values that
                the monitor gives may help get a certain mode validated.
                On the other hand, this may be dangerous if you do not
                know what you are doing.  Default: Use EDIDs.

---

### Post by KillerBOB on 2005-08-18
[QUOTE=Dolphin]I simply cannot figure this out.  My monitor at native res will do 75hz.
In ubuntu, I couldn't change it from 60.  It was a small worry I glanced at once in awhile.  I wanted to get it fixed but it wasn't dire that I do immediately.

Now I've installed the latest ATI drivers and it dropped my refresh to 47!??  What the heck??  I've editted my xorg.conf until I'm blue in the face.  No change I make makes any difference.

Here's the pertinent info in my xorg.conf

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 (R420 JK)"
	Driver		"fglrx"
	Option		"UseInternalAGPGART" "no"
	BusID		"PCI:1:0:0"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-63
	VertRefresh	56-70
	Modeline	"1280x800@70" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 (R420 JK)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

And my monitor specs.

Horizontal Freq - 30-63 kHz
Vertical Freq - 56-75 Hz


Please help me before I pull out my hair.  Thank you.[/QUOTE]

Hi! As far as I can tell, assuming the modeline you have is correct, you should  make this section look like this:

```
SubSection "Display"
		Depth		24
		Modes		"1200x800@70" 
	EndSubSection
```
That would give you 1200x800 at 70 Hz (hopefully). Generate modelines for other resolutions with:

```
gtf 1024 768 75
```

I hope this helps, best of luck!

---

### Post by schdefan on 2005-08-18
Also like you, I was having problems with refresh rates. After editing the xorg.conf ending up in total confusion about the parameters i often called this 
```
sudo dpkg-reconfigure xserver-xorg
```
and X was working very well after that.

Maybe that helps
schdefan

---

### Post by Dolphin on 2005-08-19
Thanks for the help so far guys.  Still no luck so far though.

I tried this - sudo dpkg-reconfigure xserver-xorg - and it made my X a-splode.  I'm sure due to incorrect settings on my part.

---

### Post by Dolphin on 2005-08-19
[QUOTE=KillerBOB]Hi! As far as I can tell, assuming the modeline you have is correct, you should  make this section look like this:

```
SubSection "Display"
		Depth		24
		Modes		"1200x800@70" 
	EndSubSection
```
That would give you 1200x800 at 70 Hz (hopefully). Generate modelines for other resolutions with:

```
gtf 1024 768 75
```

I hope this helps, best of luck![/QUOTE]


I didn't see this post.  Back to running at 75hz thanks to you.  You win the prize!  Thanks. :D

---

### Post by KillerBOB on 2005-08-19
Dolphin, I'm just happy that I could help  ;-)  This forum has given me so much, it's good to give something back.

take care

---


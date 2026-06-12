---
title: "Sign in screen too big"
date: 2009-01-23
forum: General Help
---

### Post by gilloz on 2009-01-23
After going through the procedures to correct my monitor resolution, I now have a problem with the sign in screen.  It appears to be zoomed in, in that the sign in box is at the lower right corner with only the words User showing or Password showing.  It use to be in the center of the screen.  Where do I look to correct this problem?   Thanks

---

### Post by stephan0h on 2009-01-23
maybe you have wrong dpi settings.

---

### Post by gilloz on 2009-01-23
Thanks stephan0h for your reply.  Ok, so where do I go to change this dpi?

---

### Post by stephan0h on 2009-01-23
I'm using kubuntu, and there it's in system-settings, desktop, fonts. Normally the dpi-values are derived from your graphics-card and monitor (defined in xorg.conf) - but you can override the automatic values in system-settings. 
hth,
stephan

---

### Post by gilloz on 2009-01-23
Well, I was able to change the dpi value down, but all that did was to change the font sizes smaller.  It did not affect the sign in screen at the beginning.

---

### Post by stephan0h on 2009-01-23
ok, I apologize, this was then no solution to your problem :(

---

### Post by gilloz on 2009-01-23
Thats OK stephan0h, I appreciate your responses.  If anyone else is looking at this post, my screen setup is good, with the exception of my sign in screen.  What deterines the size of the screen?  I noticed that after I sign in blindly, the monitor makes a clicking sound and my desktop comes in normal.  For me that is 1024x768(17" monitor).  Any comments?

Added info:  Can someone, anyone, show me a or their typical Screen Section of their xorg.conf file just to see how it looks compared to mine.  I have an nvidia Geforce 6200, Sony Trinitron 17" using Ubuntu Hardy.

---

### Post by blueshiftoverwatch on 2009-01-23
> **gilloz said:**
> I now have a problem with the sign in screen.  It appears to be zoomed in, in that the sign in box is at the lower right corner with only the words User showing or Password showing.  It use to be in the center of the screen.  Where do I look to correct this problem?   Thanks
This probably isn't the solution. But you could try holding down the CTRL button while hitting the minus button on the numpad. I do that after exiting out of a fullscreen program that causes my desktop to get zoomed in because the program's resolution is lower than that of my desktop's.
> **gilloz said:**
> Can someone, anyone, show me a or their typical Screen Section of their xorg.conf file just to see how it looks compared to mine.  I have an nvidia Geforce 6200, Sony Trinitron 17" using Ubuntu Hardy.
Here is the screen section of my Xorg.conf file. Although if mine doesn't look like yours it may be because I used the program "nvidia-settings" to configure my display settings. But here you go anyway:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1600x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```

---

### Post by gilloz on 2009-01-24
Thanks blueshiftoverwatch for the response and file.  Yeah, yours is a bit different from what I have, but your comment on using the nvidia-settings helped to get my resolution even better then I had it.  I still can't figure out why my Sign In screen is so big, or what makes it so big.  I can no longer see the sign in window.  I just enter my user name and password.  Only the letters UB from Ubuntu appear in the lower Right corner and thats it.  But anyway, thanks for your help.  Have a good weekend.

---

### Post by dcstar on 2009-01-24
> **gilloz said:**
> Thanks blueshiftoverwatch for the response and file.  Yeah, yours is a bit different from what I have, but your comment on using the nvidia-settings helped to get my resolution even better then I had it.  I still can't figure out why my Sign In screen is so big, or what makes it so big.  I can no longer see the sign in window.  I just enter my user name and password.  Only the letters UB from Ubuntu appear in the lower Right corner and thats it.  But anyway, thanks for your help.  Have a good weekend.

It is usually because the system has not being able to correctly detect the maximum screen resolution correctly. Try adding the following option```

``` to you xorg.conf file:

Section "Screen"
.......
    Option         "UseEdidDpi" "False"

---

### Post by gilloz on 2009-01-24
Thanks dcstar for your response.  Well, it didn't make a difference entering that option.  See my Screen section below.  Is it in the right place?  Thanks again.


Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Option		"UseEdidDpi" "False"
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1024x768@75"	"1024x768@70"	"1024x768@85"	"1024x768@60"	"832x624@75"	"1024x768@43"	"800x600@60"	"1152x864@75"	"800x600@85"	"1280x1024@75"	"800x600@75"	"1280x960@60"	"800x600@72"	"1280x960@85"	"800x600@56"	"1280x1024@85"	"640x480@85"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1600x1200@75"	"1600x1200@70"	"1792x1344@60"	"1856x1392@60"	"1920x1440@60"	"2048x1536@60"
	EndSubSection
EndSection

---

### Post by gilloz on 2009-01-24
Here is an update.  Finally solved my problem.  Removing Modes and Modelines that I know I would not need, plus making the adjustments in "nivdia-settings" seemed to have made the difference.  Thanks to all who responded and helped.

---


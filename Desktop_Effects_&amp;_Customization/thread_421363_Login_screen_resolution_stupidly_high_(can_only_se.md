---
title: "Login screen resolution stupidly high (can only see part of the screen)"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by pmmike on 2007-04-24
as the title suggests, my login screen has got what appears to be a stupidly high resolution on it, so i can only see part of the screen. Luckily this happens to include the login box but pretty much nothing else.

I have reconfigured xorg.conf a million times and set all the resolutions so they are supported by my monitor but still no result...

I am on ubuntu 7.0.4, I have an ATI Radeon x1600pro graphics card

---

### Post by pmmike on 2007-04-24
just a bump because it's pretty damn annoying!

---

### Post by t00th on 2007-04-24
I have the exact same problem with my X1600 as well.  The displayed resolution is much larger than the resolution my monitor is displaying.  The xorg.conf file only has resolutions that will fit on my monitor, yet on the logon screen...it still displays it all wrong.

---

### Post by pmmike on 2007-04-25
bumpy bump

---

### Post by Joga5000 on 2007-04-25
I have the exact same problem as well. I have an x1800xt and a 20" 1680x1050 LCD, but the login screen is some ginormous resolution where I can't even see the buttons on the bottom (only the login window is within view). I've made sure that the highest resolution listed anywhere in my xorg.conf is 1680x1050. Anybody know what's up?

PS: I did notice after I first installed my video card drivers that my gnome desktop resolution was set to 1920x1080, but I just changed the resolution back to normal from the main menu - but I guess it didn't affect the login screen.

---

### Post by jimeez on 2007-05-02
Yep, I have this exact same problem.

---

### Post by stchman on 2007-05-02
> **pmmike said:**
> as the title suggests, my login screen has got what appears to be a stupidly high resolution on it, so i can only see part of the screen. Luckily this happens to include the login box but pretty much nothing else.

I have reconfigured xorg.conf a million times and set all the resolutions so they are supported by my monitor but still no result...

I am on ubuntu 7.0.4, I have an ATI Radeon x1600pro graphics card

My nvidia card did the same thing.

In my xorg.conf I deleted all the resolutions greater than what I wanted so the line looked something like this:

"1280x1024" "1024x768" "800x600" "640x480"

I did this for each color depth.

It worked.  I just don't know how to to the refresh rate thing.

---

### Post by poper on 2007-05-06
Same here (Nvidia 6600GT). This is being discussed [here]("http://ubuntuforums.org/showthread.php?t=417862") but still no solution (for me)

---

### Post by neophyrigian on 2007-05-10
I had the same issue and tried very hard for a long time. I think I found a solution. What we all discuss is editing the resolutions in xorg.conf. Yes, this may be one important point, but there's one more thing: color depth. As a background for my experience: During the very first installation of xubuntu Feisty, I had chosen 24 as default depth. (Obviously, it was a mistake.)  Then, my desktop was not as it should be. Screen view was weird. I changed it from display settings -by trial and error method- to 1024x768@60. It was nice for the desktop. But not for login screen. Then I did many things. At last,I deleted all resolutions (all stands for every resolution, one by one) more than 1024x768 which seemed to be OK for my machine.Nothing changed for login screen. There should be something more than it. That @60 part maybe? Then I found "Incorrect Default Depth" subtitle in [an Ubuntu HowTo]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-5d4463295c9bf533f874ce1e93d5960bcf6f339f"). Stating that "Sometimes the automatic X configuration sets the colour depth to a value higher than some hardware can properly handle. To see if this is the case for you, first backup your /etc/X11/xorg.conf file." And explains the details. That's it! As proposed there I found these lines in xorg.conf:
Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 86C326 5598/6326"
	Monitor		"Genel Monitör"
	DefaultDepth	24

Changed 24 to 16. Saved. Rebooted.

My login screen is OK now.

I don't know what would the result be if I didn't delete those higher resolutions prior to editing the dept. For I don't need those higher resolutions, I am not adding them again. But at least now I am sure that with or without higher resolutions, but for me decreasing the depth to 16 is a must.

Regards.

---

### Post by poper on 2007-05-10
Thanks a lot neophyrigian, that works! After chaging colour depth, login screen becomes "normal". However I think we need a *real* solution, this one make us 24 bit colour depth unavailable. In my case, I need it since I use the Gimp for photography.
Anyway, thanks!

---

### Post by neophyrigian on 2007-05-12
You're welcome dear poper. I can't say anything about the "real solution" because of twe reasons: 1- I am not a that much technical person. 2- I'm not sure if our hardware (i.e screen itself and/or graphic card) can handle up to 16 or not. I don't know how to test it. About your "GIMP for photography" problem, if you listen a relatively novice's (that's me) ideas: 1- I'm doing some simple image manipulations via GIMP and I didn't feel the difference after changing the depth to 16 but what I do is very basic things. 2- If you know that your hardware is OK for more depth and you should use you that setting for your job, bring it back to 24. I think everything would again be OK but except the login screen. (I don't do this becuase I like a tidy login screen and I don't want my guests to think that linux can not serve us with good looking login screens.) If you are sure that your hardware is suitable for 24 let the devolopers know it by means of a bug report. Regards.

---

### Post by Lord Grover on 2007-07-25
This work-around doesn't work for me anyway - so I could do with a 'real solution' please. 
ATI Radeon X1300 - driver=ati-driver-installer-8.39.4-x86.x86_64.run

---

### Post by Depressed Man on 2007-07-25
I have this problem too on my desktop recently. It has to do with modes and virtual in the display section. For example this part of my /etc/X11/xorg.conf

```
Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    virtual 1152 768
    Modes "1152x768@60" "1024x768@60" "1280x1024@75" "1280x960@60" "1024x768@70" "1280x1024@60" "1024x768@75" "1280x960@75" "832x624@75" "1400x1050@60" "800x600@60" "1600x1200@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection
```

Normally it''s suppose to use the first one in mode (but it doesn't..oddly it use to and now it doesn't detect that resolution as a proper one even though my Ubuntu uses it as its resolution). I solved it by adding virtual to it.

Basically 

virtual resolutionx resolution y

if you wanted 1024x768 it'd be

virtual 1024 768

---

### Post by Lord Grover on 2007-07-25
I'm a bit confused by this. My desktop is running at 1680*1050 - fine - just what I want. However, my xorg.conf is thus:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"L204WT"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection
```

Am I missing something here?

Whatever ... my login screen is foobar'd!

---

### Post by pandion on 2007-07-25
Checkout my post on this thread for same problem.  Hope it helps!

[http://ubuntuforums.org/showthread.php?t=498922&highlight=login+screen+resolution&page=4](http://ubuntuforums.org/showthread.php?t=498922&highlight=login+screen+resolution&page=4)

---

### Post by Lord Grover on 2007-07-26
Thanks pandion - I'll give that a try when I get home. [-o<

---

### Post by Lord Grover on 2007-07-27
> **pandion said:**
> Checkout my post on this thread for same problem.  Hope it helps!

[http://ubuntuforums.org/showthread.php?t=498922&highlight=login+screen+resolution&page=4](http://ubuntuforums.org/showthread.php?t=498922&highlight=login+screen+resolution&page=4)

Hmm ... tried that - still no joy. :(

The installation of xgl appears to have worked; I can select gnome xgl at the greeter. Using the beryl manager I select beryl but the screen flashes once or twice then nothing - gnome/xgl resumes. No error messages (unless it's logged somewhere).
:confused:

---

### Post by pandion on 2007-07-30
So any luck?  Did the keypad method to cycle through the resolutions work for you, and did you add the "virtual" setting line/lines?

---


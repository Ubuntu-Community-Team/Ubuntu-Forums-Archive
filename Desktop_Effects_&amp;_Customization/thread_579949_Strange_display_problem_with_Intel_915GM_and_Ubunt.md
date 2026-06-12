---
title: "Strange display problem with Intel 915GM and Ubuntu 7.10"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by sadata on 2007-10-18
I'm having a very peculiar problem with my video driver. My screen resolution is set to 1280x1024 on an external monitor (connected to a Compaq nc6220 notebook). This notebook uses an integrated Intel 915GM display adapter. The only way to get the desktop effects enabled are to use the "intel - experiemental modesetting driver," so that's what I'm using.

In general, things work well (window opacity using Alt-mouse wheel works fine, etc.). However, if my mouse pointer is in the top-left 1024x768 pixel region of the screen, the desktop magnifier (by holding down 'Windows' or 'Super' key and rolling mouse wheel) only magnifies the top left corner (the 1024x768 region) of my screen. Likewise, if I move the mouse pointer outside of the top left 1024x768 pixel region and into the right/bottom region of the full 1280x1024 screen, then only the right and bottom of the screen get magnified. It's almost as if there are two screens (a 1024x768 one superimposed on top of a 1280x1024 one). I have a feeling that this is somehow related to the built-in LCD panel (which has a resolution of 1024x768) and the fact that I'm using a higher resolution external monitor. The external LCD panel I'm using is a Samsung SyncMaster 940B which has a native resolution of 1280x1024.

Incidentally, this is not just a problem with the magnifier. If an application window resides entirely in the top 1024x768 region and I maximize it, it will only maximize it to 1024x768. If I move the window so that part of it overlaps into the right or bottom part of the 1280x1024 screen and then maximize it, it will maximize to the full size (1280x1024).

I've tried pretty much everything and am getting nowhere fast. The experimental Intel driver does not appear to support dual monitor configurations, so I'm forced to use the external monitor function of the laptop (Fn-F4) to get the video signal output to the Samsung monitor.

Here are the relevant portions of my xorg.conf file:

```

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by TubaTodd on 2007-10-19
I'm having the very same problem with my Toshiba laptop.  I have an Acer 22" widescreen monitor at 1680x1050. If I disable desktop effects, everything is fine. If I enable them and I try to maximize a window, it will maximize to a 1280x800 window, in order to fill the screen on my laptop. The thing is....I only use the external monitor. I think this is more of a Compiz problem than it is a driver problem. HELP!! :(

---

### Post by wireless on 2007-10-19
Hey Sadata
Im trying to get extended monitor to work with no much luck .. no hotplug. did you get yours to be hotplugable?
i have Thinkpad x60 laptop with integrated intel 945gm display adapter and external samsung syncmaster 931c . 
i can get the external to work but with a script i have to run each time, and using the "screen and graphics" messes it all up . 
any advice? 
thnx

---

### Post by TubaTodd on 2007-10-19
what script are you running? Ya know what's frustrating? I had Compiz working in harmony with Ubuntu 7.04 and now my screen is acting screwy. I've tried using the xorg.conf that 7.10 generated.....no luck. Then I tried the xorg.conf that I saved from my 7.04 install......no luck. 

Right now I have compiz disabled and everything else about my Ubuntu 7.10 experience is great. I just wish I had the desktop effects. Is there an alternate repository for installing Compiz? I wonder if that would help.

---

### Post by Nicolas Pham-Dinh on 2007-10-19
I have been having the same problem then sadata with an Aspire 3680 laptop (internal 1280 x 800) and external display Acer AL2216W (1680 x 1050), and this since I upgraded to Gutsy. I did not have this problem with Feisty. When I work on the external display, the windows keep re-sizing while I work and this is driving me nuts. It is behaving as if there were two super-imposed resolution and keeps maximizing to the top right region coinciding to the resolution of the internal display. Did anyone find a solution? Please?

---

### Post by platinumpresto on 2007-10-22
Same here... running hp xt118 in 1024x768 to external vga 37" 1366x768

[http://i166.photobucket.com/albums/u120/platinumpresto/UBUNTU/Screenshot.png](http://i166.photobucket.com/albums/u120/platinumpresto/UBUNTU/Screenshot.png)

my internal display shows up to 1024x768(the edge of the dock) but the external shows past the dock at 1366x768... when i play movies the its played fine on the internal but a back screen on the external

...and, when i goto "screen and grafic prefrences" the laptop does not detect an external display... at all... not even a regular 19" acer AL1914 by vga...

...i would select the proper settings and the app would crash/quit/close...

it seems like i dont have compiz running because i have no screen effects... but how do you turn off compiz, since thats helping i guess

---

### Post by Nicolas Pham-Dinh on 2007-10-22
h

---

### Post by sadata on 2007-10-22
Hi all. I got things to work reasonably well, but I pretty much had to forget about dual monitors. I found that when I plug-in the external monitor (the 1280x1024 Samung) and close the lid on the laptop (thus disabling the internal LCD panel), everything boots up fine.  I think that the experimental Intel modesetting driver can't support multiple monitors, so when two displays are detected it gets confused and overlays one on top of the other.  Disabling the internal LCD by closing the lid at boot time seems to eliminate the confusion and only the 1280x1024 display is detected by Compiz.  This has fixed the various desktop enhancements (display zoom, etc.) and maximizing of windows.

---

### Post by Nicolas Pham-Dinh on 2007-10-22
Here's another thing: I found that turning off the visual effects in the appearance menu solves the problem. But you don't get visual effects...

---

### Post by Nicolas Pham-Dinh on 2007-11-04
Problem solved. Here's how to: 

- Install Compiz Advanced Desktop Setting;
- Open it and go to "General Options", then "Display Settings"; 
- Uncheck "Detect Outputs";
- In "Ouputs", edit the resolution (mine was set at 800x600x0x0) to your external display's resolution (mine is now 1050x1680). 

This should solve the problem.

---

### Post by ariel on 2007-11-12
Thanks Nicolas, that helped. I'm still having problems trying to get vmware to go fullscreen but that is probably due to another problem.

---

### Post by simohell on 2008-02-08
> **Nicolas Pham-Dinh said:**
> Problem solved. Here's how to: 

- Install Compiz Advanced Desktop Setting;
- Open it and go to "General Options", then "Display Settings"; 
- Uncheck "Detect Outputs";
- In "Ouputs", edit the resolution (mine was set at 800x600x0x0) to your external display's resolution (mine is now 1050x1680). 

This should solve the problem.

This didn't work for me. I didn't try closing my laptop-lid yet (I only switch off the backlight), but both with and without the above settings my windows seem to maximize and then reduce in size to my laptop screen. Other than that the effects seem so fat to work 1600x1200 with no problem.

---

### Post by simohell on 2008-02-11
Another strange detail about maximizing:
- When I double-click the window title it "maximizes" always to the size of the laptop display.
- When I use maximize icon, I get different result based on whether the window was manually sized bigger or smaller than laptop display. If t is bigger then it maximizes properly.

---


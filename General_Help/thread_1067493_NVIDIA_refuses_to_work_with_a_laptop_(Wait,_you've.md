---
title: "NVIDIA refuses to work with a laptop (Wait, you've heard this before?!)"
date: 2009-02-11
forum: General Help
---

### Post by bgii_2000 on 2009-02-11
I'm a linux n00b, although I know how to get to the terminal, and I know what "sudo" and "vi" do (oh, and "shutdown", but we're not counting).  I also know how Google works.

So,

I've tried multiple solutions including reinstall, fixing, apt-get, blah blah trying to get the NVIDIA series 96 driver to work on my laptop.  The laptop screen is physically something like 969x768, but displays a native 1024x768 area.  The NVidia driver refuses to acknowledge this, however, and insists on displaying the XServer (and its children) in a hideous, stretched out 800x600.  A viewing of the startup log reveals that it skips the 1600x1200 and 1024x768 resolutions as unsopported (though the default driver handles this resolution just fine).

I've tried Envy, and every other combination of fixes I could think of or find via Google, but nothing works (else I would not be here).  Through my research, it appears to me that if I could only get the right code to stick in the xorg.conf file, I'd be set.  Unfortunately this code is nowhere to be found.

I'd like to join the ranks of Ubuntu proselytizers, but until I get this worked out, I'm afraid that I cannot, in good conscience, endorse a product that works worse than my Windows box.

Thanks,
Brad

---

### Post by cariboo on 2009-02-11
I  would suggest that you make sure you are fully updated, make sure to comment out any ppa's you have enabled. Then remove everything related to Nvidia first. Go to System-->Administration-->Synaptic Package Manager and type Nvidia in Quick Search, then mark all the installed packages for complete removal.  Once everything is uninstalled press Ctrl-Alt-Backspace to restart X. Once you are back to the desktop go to System-->Administration-->Hardware Drivers and install the recommended Nvidia driver.

Jim

---

### Post by jocko on 2009-02-12
> **bgii_2000 said:**
> Through my research, it appears to me that if I could only get the right code to stick in the xorg.conf file, I'd be set.  Unfortunately this code is nowhere to be found.
I think I know what code you need...
You may need to add your screen's horizontal sync range and vertical refresh rate range to xorg.conf.
Try to find the specifications for your screen (either in your laptop manual, on the laptop manufacturers home page or the manufacturer of the actual screen).
If you manage to find it, try this:
```
gksudo gedit /etc/X11/xorg.conf
```
Find the "Monitor" section and add these lines:
```
    HorizSync       [COLOR=Red]30.0 - 75.0[/COLOR]
    VertRefresh     [COLOR=Red]60.0[/COLOR]
```
But use the correct values for your screen instead of the red ones.
I'm not sure this will help, but it helped me to set the correct resolution on my old monitor which wasn't properly detected.

---

### Post by bgii_2000 on 2009-02-15
So, I completely removed every entry in the package manager that had anything to do with NVidia.  Then did a clean install, also updated Ubuntu.

I took a look in the xorg.conf file and the proper h and v sync values are already in place.  And still...

```
(II) NVIDIA(0): NVIDIA GPU GeForce4 420 Go at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 16384 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.41.c7
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 420 Go at PCI:1:0:0:
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 224.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "969x768"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
```

I think I could easier diagnose the problem if I could get more verbose logging setup, but I can't find how do it, or the lines to add, or where to add them.

---

### Post by jocko on 2009-02-15
Your problem seems to be that you need to set up modelines for your monitor in xorg.conf:> **bgii_2000 said:**
> ```
[COLOR=Red](WW) NVIDIA(0): No valid modes for "969x768"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.[/COLOR]
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
```

I don't know exactly how to do that, but this command is supposed to give you a correct modeline for 969x768@60Hz:
```
gtf 969 768 60
```
Google around to see examples of where and how to add modelines in xorg.conf.
Also post your xorg.conf here, in case someone can see something to change.

---

### Post by bgii_2000 on 2009-02-15
I salvaged some modelines from a session log booted in the std xserver driver, I gonna try those first (since they seemed to work, or indicate compatibility with this screen).  **Jocko**, I've used gtf in my quest to set this thing right, adding modelines generated from gtf didn't do jack ****, so I'm gonna try these first.  Meh, maybe I'm doing it wrong or something...

I gotta say though, guys:

If I had been able to install WinXP, I wouldn't be having this problem right now.  I mean, I love OSS, and free as in freedom and all that jazz, but this is seriously pissing me off...

lol, not that it's any of all y'all's fault or anything, just the collective fault of linux fanboys out there who can't seem to understand why anyone would ever choose anything over their beloved holy penguin.

EDIT:

right, xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:37:20 PST 2008

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Unknown"
	HorizSync       30.0 - 110.0
	VertRefresh     50.0 - 150.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	Option	"UseDisplayDevice"	"DFP"
	SubSection "Display"
		Depth       24
		Modes      "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	Option         "UseEDID" "1"
	Driver	"nvidia"
EndSection
```

Is there something hugely obvious here that I'm totally missing because I'm a n00b, or what?

---

### Post by bgii_2000 on 2009-02-18
So, I managed to get X to start with logverbose 6 on (I killall'd gdm then startx -- -logverbose 6)

I've tried a few things with this new toy.  I tried starting with the modelines in place.  Got some messages about a pixelclock overrun.  Removed the modelines that were apparently offending nvidia.

Tried again, this time I got something like:

Validating Mode "1024x768_60"
Mode (1024x768 @ 60) Mode Source: X Configuration file
Hsync, HStart : blah lbah numbers nubmers
HEnd, HTotal : ditto ditto
VSync, VStart : ...
...
..
...
Mode Validation failed Resolution too large
Max: 969x768

I woulda copied the file but couldn't figure that out.

Brilliant part is, that if you try USING 969x768 it says that 969 is not a multiple of 8.  Nice.

Also, the pixelclock thing is a bit confusing.  Elsewhere in the log (as long as the nvidia driver is disabled) the pixel clock limit is 230 MHz.  However, once the driver is enabled the limit is 70 MHz.

I've also tried UseEDID "0" to make nvidia ignore the monitor's info, but this makes no difference, except that the driver seems even more confused, forces one of the overscanned modes, whacks out the screen, and seems to think that the native resolution of the screen is 640x480.

I really don't get this.  The monitor behaves just fine using the standard X driver.  It displays 1024x768, and doesn't bat an eye at pixel clock numbers or scan rates.  It's not like I'm using some Voodoo 4 card from the 1990s or something.  This is NVidia.

---


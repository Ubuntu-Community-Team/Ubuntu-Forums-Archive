---
title: "Dual monitor display settings reset on logout"
date: 2005-12-31
forum: Desktop Environments
---

### Post by hbj on 2005-12-31
I am running Kubuntu Breezy with dual 1280x1024 monitors.  In the KDesktop dialog under Display/Size & Orientation I set the screen size to 2560x1024 and I have "Apply settings on KDE startup" and "Allow tray application to change startup settings" checked.

This works great - the desktop extends across both monitors and applications that are maximixed fill one monitor.

However, when I log out and log back in, the desktop resets to 1280x1024 and I have to go through the configuration again to get KDE to use both monitors.

One thing I have noticed - in the 'screen size' selector, there are options for 1280x1024, 1024x768, and so on to lower resolutions.  The 2560x1024 setting appears at the bottom of the list which seems out of place.  I can't recall if this is something I added manually at some point to a configuration file - in any case I can't find it again.

Any idea why it isn't remembering my settings after I log out and back in or any idea of things to try?

---

### Post by short4lif2 on 2006-01-01
How did you get the xserver to recognize your second monitor? i can not seem to do this properly

---

### Post by hbj on 2006-03-23
Below is my current xorg.conf with the official ATI driver 8.23.7.  I have two 1280x1024 monitors.  Both monitors work, I can drag windows from one to the other, and when I maximize a window it fills just one monitor.  Xinerama and DRI are both working and fgl_glxgears get about 600 FPS.

When I log out of KDE and log back in, I still need to reset my display resolution each time to get the desktop to span both monitors.  After doing that it works fine until I log out.  Again when I log in I need to reset the display resolution.

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
   # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"record"
	Load	"type1"
	Load	"vbe"
   Load 	"GLcore"
   SubSection "extmod"
	  Option "omit xfree86-dga"
	EndSubSection
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Graphics Adapter0"
	Driver		"fglrx"
   BusID       "PCI:1:0:0" 
   #Option      "mtrr"                       "off"
   Option      "VideoOverlay"               "on"
   Option      "OpenGLOverlay"              "off"
   Option      "UseInternalAGPGART"         "off"
   Option      "ForceGenericCPU"            "on"
   Option      "EnablePrivateBackZ"         "on"
   Option      "DesktopSetup"               "Horizontal"
   Option      "MonitorLayout"              "TMDS, CRT"
   Option      "HSync2"                     "31.5-80.5" 
   Option      "VRefresh2"                  "55-75" 
   Option      "ScreenOverlap"              "0" 
   Screen 0
EndSection

Section "Screen"
   Identifier  "Screen0"
   Device      "ATI Graphics Adapter0"
   Monitor     "Monitor0"
   DefaultDepth 24
   Subsection "Display"
       Depth       24
       Modes       "2560x1024" "1280x1024" "1024x768" "800x600" "640x480"
   EndSubsection
EndSection

Section "ServerFlags"

EndSection

Section "Monitor"
   Identifier  "Monitor0"
   HorizSync   31.5-80.5
   VertRefresh 55-75
   DisplaySize 676 270
   Option      "DPMS"
EndSection

Section "ServerLayout"
	Identifier	  "Default Layout"
	InputDevice	  "Generic Keyboard"
	InputDevice	  "Configured Mouse"
   Screen        "Screen0"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by hbj on 2006-04-20
I know it's a little bit overkill, but wiping out my .kde directotry and letting the config files rebuild solved the problem.  Now KDE automatically works with my big desktop.  Still wish I knew what was causing the problem.....

---


---
title: "SiS 3d"
date: 2005-01-14
forum: General Help
---

### Post by aranbanjo on 2005-01-14
Hello World
I'm trying to have 3d acceleration on a SiS 630.
According to [Thomas Winischhofer site](http://www.winischhofer.net/sisdri.shtml) I'm sure SiS 630 is supported for 3d acceleration  8) 
If ```
modprobe sisfb
``` runs well, I don't know how to enable it in the kernel configuration, neither to enable SiS DRM as a module (not statically) into the kernel.
Looking at /etc/X11/xorg.conf, I've "SiS generic" , then I think AGP support is enabled
```
On SiS 630/730 and assumingly 540, this is "SiS generic"
``` 
Assuming I'll learn to recompile and install the kernel, I don't know in which line of /boot/grub/menu.lst write this line (or similar)
```
video=sisfb:mode:1024x768x16,mem:12288
``` 
Moreover, may I need to add the option ```
"MaxXFBMem" "12288"
``` to Xorg config file and, if yes, where?
I know it sounds a little bit complicated, but I'm far to give up!!!
Thank you for any help,
Maybe take a look to my xorg.conf
```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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
Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"PS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Scheda video generica"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Generico"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Scheda video generica"
	Monitor		"Monitor Generico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Generic Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by aranbanjo on 2005-01-20
I've partially solved my problems.
Now I've hardware accelereration!!!
I've also found repositories for Debian\Ubuntu:

deb [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./

deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./

But still some problems: black screen  :-( 
if I run glxgears 
610 frames in 5.0 seconds = 122.000 FPS
491 frames in 5.0 seconds = 98.200 FPS
803 frames in 5.0 seconds = 160.600 FPS
803 frames in 5.0 seconds = 160.600 FPS
846 frames in 5.0 seconds = 169.200 FPS
760 frames in 5.0 seconds = 152.000 FPS
801 frames in 5.0 seconds = 160.200 FPS
722 frames in 5.0 seconds = 144.400 FPS

that's right, but I don't see anything in the window....
Does anyone can explain me why?

---

### Post by Viro on 2005-01-20
That output from glxgears don't look like you've got 3D acceleration. I get about 140 fps on my laptop without 3D acceleration.

---

### Post by aranbanjo on 2005-06-28
Solved!!!  :) 
> Allright guys, your constant nagging and ranting about non-functional
DRI with newer Linux kernels now has gone far enough.

Smile

Therefore I spent the entire night debugging the sis DRI driver...
successfully. An updated driver is at 

[http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz](http://www.winischhofer.net/sis/sis_dri.so_6.8.2.tar.gz)

...

It is for X.org 6.8.2 and has been compiled with gcc 3.3.6. 
[screen shot](http://www.flickr.com/photos/69845370@N00/21930991/) 
Cheers.

---

### Post by irkab1rka on 2005-07-06
Quoted from [http://www.winischhofer.net/index.shtml](http://www.winischhofer.net/index.shtml)

> 
Installation:

    * Find out which version of X.org/XFree86 your system is running. Do so by typing X -version in the console.
    * Download the X.org/XFree86 driver binary archive (sisusb_drv.o_XVERSION_GCCVERSION_VERSION.tar.gz) for your version of X.org/XFree86. Save the downloaded file in any directory, for example your home directory. Please note: To install this file, you need to be root.
    * Extract the downloaded archive file and ignore eventual "ignoring trailing garbage" warning messages during extraction. The archive contains only one file named "sisusb_drv.o".
    * Copy "sisusb_drv.o" to /usr/X11R6/lib/modules/drivers/.
    * Configure and (re-)start X.org/XFree86.


---


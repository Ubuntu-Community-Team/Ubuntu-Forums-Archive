---
title: "Karmic, color depth, and all that."
date: 2010-03-11
forum: Desktop Environments
---

### Post by BioTronic on 2010-03-11
Greetings. I am running Karmic Koala on a Dell Precision M90, and have some problems with my color depth, or at least that's what I believe.

I have googled this problem numerous times, reading a lot about /etc/X11/xorg.conf, and have created numerous files in that location, with all manners of (probably) valid contents. I have yet to try invalid contents, in the hope that Linux is reading the file, and doing so would crash the system.

This is my current xorg.conf, after many iterations:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "dri2"
	Load  "dri"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "G71GL [Quadro FX 3500]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Now, is there some other place to change this? Am I doing this right? Should I sacrifice more virgins to Cthulhu, or is Hastur the one to ask in these situations?

---

### Post by asmoore82 on 2010-03-11
googling "xorg.conf" will more than likely yield out-dated results.

Modern *buntus should be able to run 100% functional with no "xorg.conf" at all.

What is your original "possibly color-depth" problem?

You might want to go ahead an check/post the output of ```
xrandr
```

---

### Post by BioTronic on 2010-03-11
> **asmoore82 said:**
> googling "xorg.conf" will more than likely yield out-dated results.

Modern *buntus should be able to run 100% functional with no "xorg.conf" at all.

What is your original "possibly color-depth" problem?

You might want to go ahead an check/post the output of ```
xrandr
```

Sorry, I forgot including the actual problem. :p It seems I'm running in 16-bit colors, and I want 24-bit.

xrandr output:
```
Screen 0: minimum 640 x 480, current 1920 x 1200, maximum 1920 x 1200
default connected 1920x1200+0+0 0mm x 0mm
   1920x1200      60.0* 
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       60.0  
   1280x960       60.0  
   1360x768       60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.0     56.0  
   640x480        60.0  

```

---

### Post by asmoore82 on 2010-03-11
could you check this
```
cat /var/log/Xorg.0.log | grep -i depth
```
or maybe just post the whole log if that doesn't say anything

---

### Post by BioTronic on 2010-03-11
Right. Output:
```
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(--) Depth 24 pixmap format is 32 bpp
```

it seems to me it is running in 24-bit. Still, image quality seems to indicate otherwise, compared to my friend running a very similar setup on a machine of the same make and model. Specifically, a rendered sphere has obvious 'banding' of colors on my screen, none on his. Same drivers, same Ubuntu version. Only thing I can remember being different is his is installed on his NTFS Windows 7 partition.

---

### Post by marek. on 2010-05-24
> **BioTronic said:**
> Right. Output:
```
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(--) Depth 24 pixmap format is 32 bpp
```it seems to me it is running in 24-bit. Still, image quality seems to indicate otherwise, compared to my friend running a very similar setup on a machine of the same make and model. Specifically, a rendered sphere has obvious 'banding' of colors on my screen, none on his. Same drivers, same Ubuntu version. Only thing I can remember being different is his is installed on his NTFS Windows 7 partition.


Hey, I have solution for you.
I have Dell m90 also, and I had exactly same issue as you with nv xorg driver.
What you need to do is to add:

        Option     "FPDither"   "1"

to you "Device" section.

Good luck! ;)

---


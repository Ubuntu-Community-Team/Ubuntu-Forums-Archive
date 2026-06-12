---
title: "Compiz - no window borders on 2nd monitor"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by jimbob on 2007-10-28
I guess the title says it all.  Everything works great on both monitors - ie cube rotation, cube transparency, etc. just no window borders on the second monitor.
Anyone else experienced this yet?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by jimbob on 2007-10-29
I guess nobody has experimented with this yet ....

---

### Post by kondyj on 2007-10-29
hmm..you dont say much about your configuration and HW.

I finally got compiz/dual-screen to work with ATI X1650 Pro & ubuntu 7.10. And i have windows border on second monitor. Just uploaded this if someone dont belive me. ;-) I dont have gnome panels on second monitor (but i dont want them).

[http://www.youtube.com/watch?v=oyoNCqwZX38](http://www.youtube.com/watch?v=oyoNCqwZX38)

---

### Post by jimbob on 2007-10-30
I have an Acer AL2416W 24" widescreen and a Sony SDM_51 19" driven by an Nvidia GeForce 6600GT AGP graphics card.

It looks like you have Xinerama turned on since you are able to drag the same window from left to right across screens.  If I do that my window will wrap around the cube to the right and cause the cube to flip (which is what I want).

I have Gnome taskbars on both screens and can put different applets on them as I wish and rotate the cubes independently of each other.  If I have Firefox running on the left screen though and I try to open it on the right one I get a message that it is already running somewhere else.  However I can open as many instances of it as I want on the same screen (either one).  Wierd eh?  

Here is my xorg.conf file in case you want to look at it:

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0"  0 0
        Screen      1  "Screen1"  RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
#        Option         "Xinerama" "off"
#        Option         "Clone"    "off"
#        Option         "Twinview" "on"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "extmod"
        Load  "dbe"
        Load  "dri"
        Load  "glx"
        Load  "record"
        Load  "xtrap"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "ACR"
        ModelName    "Acer AL2416W"
        HorizSync    24.0 - 80.0
        VertRefresh  49.0 - 75.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "SNY"
        ModelName    "SDM-S81"
        HorizSync    28.0 - 65.0
        VertRefresh  48.0 - 65.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "NVIDIA GeForce 6600GT"
        BusID       "PCI:1:0:0"
        Option      "UseDisplayDevice"  "DFP"
        Screen      0 
EndSection

Section "Device"
        Identifier  "Card1"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "NVIDIA GeForce 6600GT"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" 
        EndSubSection

EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth         24
                Modes         "1280x1024"
        EndSubSection
EndSection

---

### Post by francky_51 on 2007-10-30
Same problem here :(
I have a P4 3Ghz with a nvidia 7600 GS.
Separate x screen configuration : samsung lcd tv on the left and generic 19" lcd monitor on the right.
So there are no borders on my tv screen and on my first screen (the 19" lcd monitor)  there is a short delay between opening a window and the actual appearing of the window (about 1,5 seconds). Even with menus or popups.
This is my xorg.conf :

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
	Load	"type1"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"dbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"ZAxisMapping"	"4 5"
    	Option		"Emulate3Buttons"	"true"
    	Option		"Buttons"	"12" 
    	Option		"ButtonMapping"	"1 2 3 6 7 8 9 10 11 12"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "GRE LM19T"
    HorizSync      30.0 - 80.0
    VertRefresh    50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Option	   "AddARGBVisuals"	"True"
    Option	   "AddARGBGLXVisuals"	"True"
    Option	   "TripleBuffer"	"True"
    Option	   "NoLogo"	"True" 
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Option	   "AddARGBVisuals"	"True"
    Option	   "AddARGBGLXVisuals"	"True"  
    Option	   "TripleBuffer"	"True"
    Option	   "NoLogo"	"True" 
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1280x1024 +0+0; DFP: 1024x768 +0+0; DFP: 832x624 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1360x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by Nixus_Maximus on 2007-11-03
I have the same problem with nvidia FX5700, monitor and tv separate x-screen configuration. Seems to be a compiz/nvidia bug?

Cheers NM

---

### Post by francky_51 on 2007-11-05
I used compiz-fusion on feisty with the same X configuration and everything was ok.
Is there a bug report open for this problem ?

---

### Post by Linder on 2007-11-05
Same issue here. Two monitors, one 17'', one 22''. 

22'' is primary, and window management is slow (short delay in opening windows after click), and window borders work.

17'' secondary screen. Fast and agile, however, no borders (decorations). 

Using gtk-window-decorator in command under Window Decoration in CSSM. Emerald NOT installed.

---

### Post by Aoestein on 2007-11-10
I'm experiencing the same problem, Dualscreen setup with two X servers.
No windowborders on the secondary and slow menus on the primary.
No Xinerama enabled.

Is this reported as a bug?

Any solution for this?

Hope for a quick fix.

Edit: GFX-card : Nvidia 6800LE

---

### Post by francky_51 on 2007-11-12
I didn't find a bug report on launcpad.
As my english is not perfect is it possible that one of you post a bug report ?
I disabled 3d effect for the moment :(

Thx

---

### Post by jimbob on 2007-11-12
Where did you find 3d effect?  I was under the impression that was not available yet.

---

### Post by francky_51 on 2007-11-13
Sorry I was thinking about visual effects but I wrote 3d effects :)

---

### Post by Rupertronco on 2007-11-13
I thought xinerama was separate x screens? Are you using twinview or xinerama? From what I understand, twinview is what I use, same desktop, 2 monitors, and xinerama is independent screens.

---

### Post by Rupertronco on 2007-11-13
> **jimbob said:**
> Where did you find 3d effect?  I was under the impression that was not available yet.

If you're talking about being able to manipulate the windows in 3-d space, than it is available, just snoop around the compiz forums, it's a little buggy right now though.

---

### Post by jimbob on 2007-11-13
No- in the Beryl manager under "Effects" there was an actual selection named "3D Effects" that could be checked.  What it did was raise the windows off the cube face when the cube was rotated so you could see their edges - very nice eye candy.  So far that particular enhancement has not been made avasilable in Compiz-fusion although I believe it will be forthcoming.

---

### Post by XioNoX on 2007-12-19
I have the same issue,
On my first screen (laptop screen) there are delay to open menu, right click, etc...
But the second screen (15" lcd) is have a normal speed.
For the compiz issue, I just do alt + F2 and run compiz --replace to have windows border.
I don't have desktop icons.
And another strange thing, I can't add a systray on the second desktop...

Thanks
XioNoX

---

### Post by jimbob on 2007-12-19
When I ran compiz --replace it gave me window borders all right but it killed compiz completely and nothing on either desktop would work after that.  So in my case the cure is worse thsn the disease.

---

### Post by Trebaruna on 2008-01-22
Just chiming in to say that I have the problem, too.
Using Ubuntu provided driver, setup seperate X screens with nvidia-settings.
Primary screen is a 19" Iiyama monitor for daily work, secondary is a 32" Samsung HDTV for movies and things. Using Gutsy 64bit.
If anyone's an answer yet, I'd be much obliged.

---

### Post by the_bob on 2008-01-30
I had the same problem.
Enable separate  X screens and Xinerama.
Solved it for me.

core2duo 
8800 GTS 320mb

---

### Post by DAE_JA_VOO on 2008-02-03
> **Aoestein said:**
> I'm experiencing the same problem, Dualscreen setup with two X servers.
No windowborders on the secondary and slow menus on the primary.
No Xinerama enabled.

Is this reported as a bug?

Any solution for this?

Hope for a quick fix.

Edit: GFX-card : Nvidia 6800LE

Exactly the same problem here.

2x 22" LCDs, nvidia 7600GT graphics.

---

### Post by cfmunster on 2008-03-13
I have the same issue - dual screens, nVidia 7300 series, no Window borders on the secondary screen and slow menus on the primary. The dropdownmenu effects are not enabled at all on the secondary screen. Here is my xorg.conf

```

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "true"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1440x900"
    HorizSync       31.5 - 56.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA1912wSERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA1912wSERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72 [GeForce 7300 SE]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72 [GeForce 7300 SE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: 1440x900@60 +0+0; CRT-1: 1280x800@60 +0+0; CRT-1: 1280x720@60 +0+0; CRT-1: 1280x768@60 +0+0; CRT-1: 800x600@60 +0+0; CRT-1: 800x600@56 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: 1440x900@60 +0+0; CRT-0: 1280x800@60 +0+0; CRT-0: 1280x720@60 +0+0; CRT-0: 1280x768@60 +0+0; CRT-0: 800x600@60 +0+0; CRT-0: 800x600@56 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by cfmunster on 2008-03-13
I found a solution to the problem of dual monitors and no window borders, check this thread for autocrosser's post and sample xorg.conf.

[http://ubuntuforums.org/showthread.php?t=536045]("http://ubuntuforums.org/showthread.php?t=536045")

The only funny thing I see so far is bits of the secondary screen failing to re-paint correctly at times, but it seems like a minor annoyance more than anything.

EDIT:

OK, I changed from SWCursor to HWCursor and my painting problem went away. What was happening was clearly a refresh rate problem with re-painting the screen while cursor was moving over another layer, like a menu. In my xorg.conf, in the Device section, I changed:

SWCursor "true'
HRCursor "false"

to 

SWCursor "false'
HRCursor "true"

and that did the trick for me. Now Compiz Fusion works perfectly with my nv 7300 and dual LCD panels.

---


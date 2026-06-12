---
title: "Upgrade from 9.04 screen mess"
date: 2009-07-02
forum: Desktop Environments
---

### Post by pmla on 2009-07-02
LOL ...I installed 9.04 yesterday and managed to have compiz and emerald working....it was gorgeous.

But, there's always a but.

Then I activated Xinerama and Separate X Screen because I have a TV svideo connection.... and the result:

If I go to System»Preferences»Appearance»and select the Visual effects TAB
-NONE effects is selected
if I try to activate EXTRA effects I get
"The Composite Extension is not available"

Here's a list of cmds:
**************************************************
sudo lshw -C video
*-display
description: VGA compatible controller
product: GeForce 8600 GT
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia
************************************************** **
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
************************************************** **
glxinfo
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
84 GLXFBConfigs:
visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
Segmentation fault
************************************************** ***********


************************************************** *******************
#@Gamer-Ub:~$ ./compiz-check

Gathering information about your system...

Distribution: Ubuntu 9.04
Desktop environment: GNOME
Graphics chip: nVidia Corporation GeForce 8600 GT (rev a1)
Driver in use: nvidia
Rendering method: Nvidia

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [FAIL]
Checking for non power of two support... [FAIL]
Checking for composite extension... [FAIL]
Checking for FBConfig... [FAIL]
Checking for hardware/setup problems... [FAIL]

There has been (at least) one error detected with your setup:
Error: Another compositing manager in use.

Would you like to know more? (Y/n) y

The default window manager of GNOME has its own compositing manager to
provide basic desktop effects.
If this one is in use, Compiz will not be able to run.

Do you want to disable GNOME's compositing manager? (Y/n) y
#@Gamer-Ub:~$ Xlib: extension "RANDR" missing on display ":0.0".

************************************************** ******
My xorg:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings: version 1.0 (buildd@palmer) Sun Feb 1 20:21:04 UTC 2009

#
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig: version 1.0 (buildmeister@builder63) Mon Mar 23 15:33:27 PST 2009

Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" 1680 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Files"
RgbPath "/usr/X11R6/lib/X11/rgb"
FontPath "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/misc/"
FontPath "/usr/X11R6/lib/X11/fonts/Type1/"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi/"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
Load "dbe"
Load "extmod"
Load "type1"
Load "freetype"
Load "glx"
EndSection

Section "ServerFlags"

Option "Xinerama" "1"
EndSection

Section "InputDevice"

# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Acer AL2216W"
HorizSync 30.0 - 82.0
VertRefresh 56.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Unknown"
ModelName "TV-0"
HorizSync 30.0 - 82.0
VertRefresh 56.0 - 76.0
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8600 GT"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8600 GT"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "AllowGLXWithComposite" "True"
Option "RenderAccel" "True"
Option "AddARGBGLXVisuals" "True"
Option "TwinView" "0"
Option "TwinViewXineramaInfoOrder" "CRT-0"
Option "metamodes" "CRT: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "TV: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
************************************************** **************


LOL...what a mess @least the 19" LCD and the svideo output to the 37" LCD screen are still working.

I tried to revert to original settings and get compiz to work even if the second monitor (svideo »»» LVD TV) would not work.... but could not????

My ideia was to have 2 xorg config files that I would load accourding to my needs.
- 1 file to have the second screen running TV out using Xinerama Seperate X Screen
- 1 file just for one screen and to a compiz emerald running.



Can anyone help?

---

### Post by Jarkycat on 2009-07-02
Not sure how much help I'll be, just wanted to say that I've never had luck with Xinerama working well in opengl beyond the very first screen.   Maybe times have changed...

Ok, are you able to run glxgears on any of the screens currently?

Also, maybe try a working setup with Twinview instead of Xinerama if you really need compiz.

---

### Post by pmla on 2009-07-02
#@Gamer-Ub:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

glx missing??? how can it be missing if I'm running nvidia proprietary drivers 180???????

About twinview, I need the same screen res on both screen right? Because the TV LCD only outputs a max 1366 x 768 pixels and my 19" monitor 1680x1050.

I don't want to run my main monitor at such a low res.

---

### Post by Jarkycat on 2009-07-02
I'm certain you can run different resolutions under twinview.  I don't have an working .conf right in front of me at the moment, but I've run 1600x1200 on 20" alongside a 21.5" at 1680x1050 before.

Try it again with Twinview and see if it'll let you change the resolutions from the gui.  If not, I do recall it just being another part of the display line in the xorg.conf file.

I'll try to find some examples for different resolutions w/Twinview.

---

### Post by pmla on 2009-07-02
Just did what you suggested....
Now I go to System»Preferences»Appearance»and select the Visual effects TAB
-NONE effects is selected
if I try to activate EXTRA effects I get
"Desktop effects could not be enabled"
?????
Could it be the restricted drivers????
I still get:
*****
#@Gamer-Ub:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
*****
#@Gamer-Ub:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
84 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault








**xorg looks like this now:**
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

#
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by Jarkycat on 2009-07-02
Can you try disable the composite extension and see if that lets you bring up glx at all?

Set composite to 0 in the xorg.cfg

Section "Extensions"
Option "Composite" "0"
EndSection

---

### Post by pmla on 2009-07-02
Changed:
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

#
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "0"
EndSection


After a restart nothing changed. Ufffff, don't know what to try?!?!

---

### Post by Jarkycat on 2009-07-02
Ug, I'm really not sure where to go from this point.

How about removing a few more variables to rule them out.

Try commenting out the following (with a hash):
ex:
#Option "AllowGLXWithComposite" "True"
#Option "RenderAccel" "True"
#Option "AddARGBGLXVisuals" "True"

Reboot and see how it does.   I'm comparing your .conf against one of mine with an Nvidia 9600 GT (close but not quite the same) and I'm just trying to eliminate some of the excess entries and differences.



If that still fails...

Would you be willing to try reinstalling the nvidia drivers again?   I don't know why it would say that glx entensions are not enabled on your _primary_ display when the card is capable (8600gt)... and you said it was all working previously and you do have the right driver installed/180 series.

Sort of a long shot, but how about trying the nvidia install again but this time from EnvyNG?

Have EnvyNG uninstall the nvidia drivers, then have it apply version 180.44 again.  EnvyNG is in the package manager.  You may want to install the qtk version unless you don't mind a text interface.

Worth a shot? maybe :)

---

### Post by Jarkycat on 2009-07-02
One other thought that I should have caught earlier.

Here is says it was running on top of the default gnome WM.

How are you running compiz?

Have you tried it with as 'compiz--replace' to kill the other windows manager?  It almost looks like you're running two managers.

Does the compiz-check command still look the same, even after initiating the WM with compiz--replace?



> **pmla said:**
> 
#@Gamer-Ub:~$ ./compiz-check

Gathering information about your system...

Distribution: Ubuntu 9.04
Desktop environment: GNOME
Graphics chip: nVidia Corporation GeForce 8600 GT (rev a1)
Driver in use: nvidia
Rendering method: Nvidia

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [FAIL]
Checking for non power of two support... [FAIL]
Checking for composite extension... [FAIL]
Checking for FBConfig... [FAIL]
Checking for hardware/setup problems... [FAIL]

There has been (at least) one error detected with your setup:
Error: Another compositing manager in use.

Would you like to know more? (Y/n) y

The default window manager of GNOME has its own compositing manager to
provide basic desktop effects.
If this one is in use, Compiz will not be able to run.

Do you want to disable GNOME's compositing manager? (Y/n) y


---

### Post by pmla on 2009-07-02
> **Jarkycat said:**
> Ug, I'm really not sure where to go from this point.

How about removing a few more variables to rule them out.

Try commenting out the following (with a hash):
ex:
#Option "AllowGLXWithComposite" "True"
#Option "RenderAccel" "True"
#Option "AddARGBGLXVisuals" "True"

Reboot and see how it does.   I'm comparing your .conf against one of mine with an Nvidia 9600 GT (close but not quite the same) and I'm just trying to eliminate some of the excess entries and differences.



If that still fails...

Would you be willing to try reinstalling the nvidia drivers again?   I don't know why it would say that glx entensions are not enabled on your _primary_ display when the card is capable (8600gt)... and you said it was all working previously and you do have the right driver installed/180 series.

Sort of a long shot, but how about trying the nvidia install again but this time from EnvyNG?

Have EnvyNG uninstall the nvidia drivers, then have it apply version 180.44 again.  EnvyNG is in the package manager.  You may want to install the qtk version unless you don't mind a text interface.

Worth a shot? maybe :)
**************************************

Removed:
#Option "AllowGLXWithComposite" "True"
#Option "RenderAccel" "True"
#Option "AddARGBGLXVisuals" "True"
and restart...same problem

Installed envyNG, uninstalled 180 and installed again... nothing changed
installed with envyng drivers 173 .... nothing changed
went back to version 180 with envyng... nothing changed.


Is there a way to see the kernel nvidia is using? hummm I remember trying to install beta 185 and it asked me about the kernel.

---

### Post by pmla on 2009-07-02
The latest compiz check...  with drivers 180 installed by envyng

at least I have one OK now :p


Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

*****************************

#@Gamer-Ub:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity
*****************************


Thanks for your help, have to go to bed now. I'm sure it's something stupid... user related.... ME.

If you can, we will get back at this tomorrow. Would appreciate that, another brain is better than my half brain.... Thanks.

---

### Post by Jarkycat on 2009-07-02
> **pmla said:**
> 
Is there a way to see the kernel nvidia is using? hummm I remember trying to install beta 185 and it asked me about the kernel.

Current linux kernel = uname -a
current nvidia driver = cat /proc/driver/nvidia/version


Did you see my above post about 'compiz--replace'

If you run that and then do the compiz-check, does it still stay anything about another WM present?

---

### Post by pmla on 2009-07-03
Current linux kernel = uname -a
current nvidia driver = cat /proc/driver/nvidia/version
2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

current nvidia driver = cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 


#@Gamer-Ub:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity
and it basically crashes the display...loose all window bars....had to restart



./compiz-check looks like this after a restart

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 


What about wm present? how can i check that?


also...under System»Preferences»QT 4 Settings 
Select Gui style: What option should I have selected there:
1 Desktop Settings (default)
2 CDE
3 CleanLooks
4 GTK+
5 Motif
6 Plastique
7 Windows

---

### Post by Jarkycat on 2009-07-03
also...under System»Preferences»QT 4 Settings
Select Gui style: What option should I have selected there:
1 Desktop Settings (default)

Yes, mine is set the same way there.

Well, I'm not sure what else I can help out with that won't have us running in circles.

Here's what I'd still like to try out if willing:

1) Completely remove 'compiz' in the package manager and reinstall it. Reboot, check it out.

2) Completely remove 'nvidia-glx-180' (just that one package) in the pm and reinstall it.  Reboot, check it out.

3) Try your xorg.conf barebones and then turning on twinview again, etc.   So backup the current xorg.conf and replace it with the below.  This is your original version without all the extra switches that I see.

(see below)

4) Short of someone else chiming in and helping us out... there's another forum thats not Ubuntu specific but Nvidia Linux specific that may be worth checking out @ [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&order=desc](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&order=desc)

Let's see how 1 through 3 goes.

----




Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Module"
Load "glx"
EndSection

Section "ServerFlags"
Option "Xinerama" "0"
EndSection

Section "InputDevice"
# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Acer AL2216W"
HorizSync 30.0 - 82.0
VertRefresh 56.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Unknown"
ModelName "TV-0"
HorizSync 30.0 - 82.0
VertRefresh 56.0 - 76.0
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8600 GT"
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8600 GT"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "metamodes" "TV: nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

---

### Post by pmla on 2009-07-03
I want to thank you for your support.

I lost all patience and just re-installed ubuntu again. Everything seems to be working now (twinview + compiz) just need to install emerald. Basically did what the majority of users do.... re-install ubuntu again. Which sucks.

I love open-source, specially ubuntu but have to say that there are still many problems...specially when it comes to basic 1+1 graphic card installation and drivers. It works ok if it's basic but advanced setup's....lol... need to be a ubuntu rocked scientist, which I'm NOT.

There's tons and tons of people asking for help when it comes to graphic cards, maybe ATI more than Nvidia.
I really don't know who to blame? if linux distros or the graphic card manufacturers and driver suppliers. And I really don't care.

For ubuntu and other linux distros to spread to even more users, some issues have to work smothelly.
Software should be built for STUPID USERS like ME.. not user friendly, but stupid friendly and GUI manageable. That's why there's Desktop versions with GUI.

I'm sure that when some ubuntu rocket scientist read this, he will get very upset. The truth is that only one user inside the community came forward to help me (you). Also, all the How too's are completely outdated... version 7.10 or 8.... nothing much for 9.04, not much help there.

That's just my 5cents.
Thank you again.

---

### Post by Jarkycat on 2009-07-03
Sorry we couldn't get it back without the nuke option ;) but I'm glad you have it working again.  Twinview should definitely serve your needs of 2 monitors+3d effects better than Xinerama.

And I do agree with most of your sentiments on the state of linux desktop.  It's far from perfect, but it is getting better with every release.

Take care for now.

---


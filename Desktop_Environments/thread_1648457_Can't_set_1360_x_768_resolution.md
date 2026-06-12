---
title: "Can't set 1360 x 768 resolution"
date: 2010-12-18
forum: Desktop Environments
---

### Post by pelikan on 2010-12-18
In Ubuntu 10.10, with the Nvidia Current driver (260.19.06), I have the option to set 1360 x 768 resolution (via gksudo nvidia-settings), but it doesn't work. The screen goes blank for about 10 seconds and then comes back on, reset to 1024 x 768.

I've searched this forum and internet in general for the past 5 hours but have not found a solution that worked. 

Any help would be very much appreciated.

---

### Post by Krytarik on 2010-12-18
1.) Check if your video card supports that resolution:
```
sudo apt-get install hwinfo
sudo hwinfo --framebuffer
```2.) If so, try enabling it with this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by pelikan on 2010-12-18
Thank you Krytarik.

Hwinfo does not list 1360 x 768. I tried two different Nvidia cards that I have here. This is strange because they both work at that resolution in other operating systems (older ubuntu, older puppy and XP).

I'm not sure what to do. The better of these two cards shows 1280 x 720 in hwinfo . But my monitor does not officially support that resolution. 

Any further suggestions?

Thank you.

---

### Post by Krytarik on 2010-12-18
Does hwinfo list resolutions above the desired one?

If so, then follow the guide I posted the link of.
At my machine hwinfo also doesn't list the resolution I'm actually using.

By the way, do you use a LCD or CRT, for which you want to set the refresh rate (Hz)?

---

### Post by pelikan on 2010-12-19
Yes, hwinfo lists resolutions higher than 1360 x 768. I use an LCD and want to set the refresh rate to 60 Hz.

Following the guide you posted, I created a modeline with cvt:

```
~$ cvt 1360 768
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

```

Copied it into xrandr:

```
~$ xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```

I thought maybe the small case "x" was wrong, so tried with capital "X" in 1360X768:

```
~$ xrandr --newmode "1360X768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default

```

And added it to the output with small case x:

```
~$ xrandr --addmode default 1360x768
xrandr: Failed to get size of gamma for output default

```

Added to the output with capital X:

```
~$ xrandr --addmode default 1360X768
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1360X768"
```

Here is xrandr now:

```
~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1360 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    60.0  
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
   1360x768       60.0  
  1360x768_60.00 (0x17a)   84.8MHz
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360X768_60.00 (0x18a)   84.8MHz
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz

```

Tried to set the resolution:

```
~$ xrandr --output default --mode 1360x768 --rate 60
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

---

### Post by Krytarik on 2010-12-19
Please post your current "/etc/X11/xorg.conf".

EDIT: Are you using an external monitor (with a laptop) or dual-monitor or something else different from "standard"?

EDIT 2: There are some reports that xrandr may not work properly with proprietary nvidia-drivers, I can confirm this on my machine, xrandr doesn't show the correct mode I'm currently using. So just try adding/setting the mode in the xorg.conf, like also described in the guide. You have to do this anyway to make the resolution change permanent.

---

### Post by pelikan on 2010-12-19
Thanks Krytarik.

I'm using a PC with an LCD TV as a monitor.

I'll try setting the resolution in xorg.conf.

Here is what it looks like now:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Edit: I'm lost. I tried to edit this file twice but booted into a black screen both times.

---

### Post by stevenpounders on 2010-12-20
Same problem for me. I'm using an Acer h233h 23" monitor with a Vaio VGN-T350P laptop. The monitor is using 1028x768 resolution instead of the 1920X1080 it's capable of. Tried the xrandr with the same "Failed to get size of gamma for output default message. The "/etc/X11/xorg.conf" file didn't exist so I created one with commands as specified in these forums. Then the computer just boots into a blank screen, and I have to reinstall Ubunto 10.10. Don't want to do that again!

---

### Post by pelikan on 2010-12-20
If you do boot to a blank screen after a failed xorg.conf, one option other than to reinstall is to use the install CD to boot into recovery mode. You just choose "Repair a broken system" instead of "install." Then select the partition ubuntu is on and you'll get a shell. Then use these commands to get rid of the bad xorg.conf:
```
cd /etc/X11
mv xorg.conf xorg.conf.old
exit
```

---

### Post by Krytarik on 2010-12-20
> **pelikan said:**
> Thanks Krytarik.

I'm using a PC with an LCD TV as a monitor.

I'll try setting the resolution in xorg.conf.

Here is what it looks like now:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```Edit: I'm lost. I tried to edit this file twice but booted into a black screen both times.
Did you specify the modeline following the guide and added the according selection in the Screen-section, both I don't see here?

Your xorg.conf is incomplete, at least the Monitor-section should be there, I post you mine:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-4401"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200"
    Option       "NoLogo"    "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1152x864_85 +0+0; 1152x864 +0+0; 1152x864_100 +0+0"
    Option       "AddARGBGLXVisuals"    "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```To get the HorizSync and VertRefresh values of your monitor, enter in a terminal:
```
xvidtune
```and press "Cancel"!

---

### Post by pelikan on 2010-12-21
Ok here is what I have now. It still boots into 1024x768 somehow. This is actually a very interesting process though. I enjoy learning more about this and appreciate the help.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       48.36
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1360x768_60 +0+0"
    Option         "AddARGBGLXVisuals"    "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Krytarik on 2010-12-21
You should have read this (posted before)[-X ;):
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
[COLOR=Red]    HorizSync       48.36    # is this really correct? please post the output of "xvidtune"
[/COLOR]    VertRefresh     60.0
[COLOR=Red]    Modeline                 # put the result of "cvt 1360 768" here
[/COLOR]    Option         "DPMS"
[COLOR=Red]    Option         "PreferredMode" "1360x768_60.00"
[/COLOR]EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
[COLOR=Red]    Option         "1360x768"
[/COLOR]    Option         "AddARGBGLXVisuals"    "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by pelikan on 2010-12-21
Thanks, I did read that guide. Spent hours in it, actually. I haven't posted everything I've tried. I added modelines yesterday and it didn't boot. I'll try again as per your instrucions.

Edit: Yes the HorizSync is correct. Got it from xvidtune.

Edit: Okay tried your xorg.conf. It booted, but in 1024x768:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       48.36    
    VertRefresh     60.0
    Modeline       "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    Option         "DPMS"
    Option         "PreferredMode" "1360x768_60.00"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "1360x768"
    Option         "AddARGBGLXVisuals"    "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Krytarik on 2010-12-21
Obviously I'm also just crawling the web for possible solutions.

Is your monitor connected via VGA or DVI (or something else)?:
[http://forums.nvidia.com/index.php?showtopic=73027](http://forums.nvidia.com/index.php?showtopic=73027)

If you only have that single LCD connected, try disabling the Twinview options in xorg.conf.

Uninstall the Nvidia-driver via "Additional Drivers" and rename/remove the xorg.conf, then

1.) try default "nv" driver (gets used automatically after the above steps)

2.) try 173er-version of the Nvidia-driver (install them via Synaptic if not offered via "Additional Drivers)

2.) try the proprietary drivers offered by the Ubuntu-X-Team:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by pelikan on 2010-12-21
Thanks for the suggestions. Using the NV driver, I was able to use xrandr to add a modeline and then set 1360x768 via the Ubuntu menu/System/Preferences/Monitors. That's a great start. 

The only problem is the screen is shifted to the right by about 10%. I was able to adjust my monitor a little, but not enough.

---

### Post by Green Moon on 2010-12-21
If your monitor supports it, you can try using the 'auto adjust' button if it has one. (I have that option so it adjusts perfectly every time the screen's out of range). :)

---

### Post by pelikan on 2010-12-22
Thanks Green Moon. My "Auto Adjust" button doesn't do anything, unfortuantely. 

I tried xvidtune, but get an error message when applying settings.

---

### Post by Krytarik on 2010-12-22
I wouldn't stick to the "nv"-driver, its performance is rather poor, it doesn't provide hw-accel, this was just a try, if its driver-related, obviously it is.

Try one of the remaining options next, 173er and Ubuntu-X-Team.

---

### Post by pelikan on 2010-12-22
The 173 driver offered a max res of 640x480. I changed the xorg.conf as follows and it rebooted into 1024x768. Something here is helping a little. Not sure what, exactly.

```
Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       48.4    
    VertRefresh     60.0
    Modeline       "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    Option         "DPMS"
    Option         "PreferredMode" "1360x768_60.00"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option	    "UseEdid" "False"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes        "1360x768_60.00"
    EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by pelikan on 2010-12-22
I installed the latest driver from Ubuntu-X. It give me an option to set 1360x768 in nvidia-settings. But when I set it, my screen goes blank. 

I've been trying various xorg.conf configurations but nothing has worked so far.

---

### Post by pelikan on 2010-12-22
I'm back with the NV driver for now. At least this way I can have a resolution of 1360x768. Missing one inch of the screen on the right side is acceptable until I solve this issue.

---

### Post by pelikan on 2010-12-29
I found I can use 1280x768 and the screen is centered. Not quite ideal but acceptable. I lose a tiny bit of screen real estate on both sides. 
The Nouveau video driver is working just fine for my needs. 
I used xrandr to add the modeline and put the commands in /etc/gdm/Init/Default so that my system boots with this resolution.
I'm going to call this "solved."
Thanks again for your help Krytarik :)

Here is what I did, following the advice in this thread, from [the guide recommended earlier]("https://wiki.ubuntu.com/X/Config/Resolution") and [this other thread.]("http://ubuntuforums.org/showthread.php?t=1321224"):
Used "cvt" to get my modeline:
```
cvt 1280 768 60
```
```
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```
Used xrandr to find out what my video output is called:
```
xrandr
```
```
...VGA-1...
```
Used xrandr to set new mode, add and select it:
```
xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```
```
xrandr --addmode VGA-1 1280x768_60.00
```
```
xrandr -s 1280x768
```

Then added that to /etc/gdm/Init/Default, just above "/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm"
```
# Added screen resolution commands:
# Add 1280x768 resolution
xrandr --newmode  "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
xrandr --addmode VGA-1 1280x768_60.00
# Select 1280x768 on startup
xrandr -s 1280x768
```

---


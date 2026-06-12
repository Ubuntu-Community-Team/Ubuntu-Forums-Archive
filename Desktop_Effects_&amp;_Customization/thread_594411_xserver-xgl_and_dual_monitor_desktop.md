---
title: "xserver-xgl and dual monitor desktop"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Nick Payne on 2007-10-27
After I install xserver-xgl for compiz on Gutsy, the behaviour of extended desktop across dual monitors changes. Prior to install of xserver-xgl, maximized windows maximize to one monitor or the other, and centered windows/dialogs opened centered on one monitor or the other. After install of xserver-xgl, windows maximize across both monitors, and centered windows/dialogs open split half and half between the monitors.

What's the fix for this problem? Video card is a dual head digital output nvidia 7600 and monitors are both Dell 2001fp. I didn't have the same problem when I was running Beryl on Feisty.

ps. this is x64 Gutsy

---

### Post by sinkr on 2007-10-31
Hello, I too am having this problem with 7.10 Gutsy amd64.

My setup consists of GNOME, Xgl, Compiz, and nVidia 100.14.23 (I also had this problem w/ .19).

2x MSI nVidia 8600GTs, 3x digital out to monitors (one 1920x1280, two 1280x1024).

I never tried this configuration on Feisty, but I have tinkered with nvidia-xconfig in terms of Xinerama on/off, TwinView on/off, etc. (so many changes and options that it's pointless to post my config) yet I still get the statusbar going across 3 monitors, maximize across 3 monitors, etc.


> **Nick Payne said:**
> After I install xserver-xgl for compiz on Gutsy, the behaviour of extended desktop across dual monitors changes. Prior to install of xserver-xgl, maximized windows 
[...]
ps. this is x64 Gutsy

---

### Post by planetenkiller on 2007-10-31
Same here.

I solved this problem with install the linux nvidia driver form nvidia.com (nvidia.de).
See: [http://ubuntuforums.org/showpost.php?p=3615238&postcount=2]("http://ubuntuforums.org/showpost.php?p=3615238&postcount=2")

---

### Post by uclalinux on 2007-10-31
Hey Guys this is a  topic that  bugs many people(I spend about 2 solid weeks getting mine just right) , here is a quick howto for a gentoo system, it will be the same for ubuntu, since they both use Xorg 
I have read thouge this and its is correct.

I would recommend to use the Nvidia with the Twinview option , but  learning how to make multiple x sessions is  good to know, but probably  not what you want.  

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Nvidia](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Nvidia)

ALSO You can download the "Nvidia-settings" pakage from >  aptitude install nvidia-setting, but I would still edit the xorg by hand.

---

### Post by sinkr on 2007-10-31
I've done this ad nauseum; Installing both the .19 and .23 drivers from the nVidia web site, installing the .19 and .23 drivers from Envy.

I've removed all the nvidia-* packages as some suggested, rebooted, installed the nVidia drivers all to no avail.

I'm not sure what the problem is other'n to try a Feisty install to another drive and see if this behavior shows itself and then attempt to isolate where the differences lie...

> **planetenkiller said:**
> Same here.

I solved this problem with install the linux nvidia driver form nvidia.com (nvidia.de).
See: [http://ubuntuforums.org/showpost.php?p=3615238&postcount=2]("http://ubuntuforums.org/showpost.php?p=3615238&postcount=2")

---

### Post by sinkr on 2007-10-31
I had a modicum of success (tried this previously as well), but the problem is somewhat endemic to my setup:

2x PCIe MSI 8600GTs and 3 DVI flat panels
  1- 1920x1200
  2- 1280x1024

When using TwinView I got the same bad behavior on the 8600GT that had two monitors on it (as in driven from the same GPU).  This behavior is of course the bar going across both screens and maximizing goes across two screens.  

The interesting thing is, the 8600GT that's driving the odd panel (the 3rd one) popped up with a bar of its own; This monitor did the "right thing," but that's seemingly because that monitor has a card of its own whereas the other two are shared off of one card.

> **uclalinux said:**
> Hey Guys this is a  topic that  bugs many people(I spend about 2 solid  
[...]
[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Nvidia](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Nvidia)
hand.

---

### Post by uclalinux on 2007-10-31
sinkr-

I had that same problem, I don't remember the fix, I will included a simple xorg,conf that works well and does not have your problem. 

also do you have only one session running for all three monitors or do you have two sessions, where two monitors are controlled with Twinview and the third is its own device.


here is a website for a nvidia set up
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 1
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
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
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BusID           "PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"   
Option "UseEdidFreqs" "False"
Option "MetaModes" "1280x1024,1280x1024; 1280x1024,1280x1024"
Option "UseDisplayDevice" "CRT,DFP" 
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---


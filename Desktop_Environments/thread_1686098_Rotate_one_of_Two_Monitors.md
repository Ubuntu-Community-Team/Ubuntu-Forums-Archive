---
title: "Rotate one of Two Monitors?"
date: 2011-02-11
forum: Desktop Environments
---

### Post by mattlach on 2011-02-11
Hi all,

I have searched this a few times, and there are a few posts on this topic with disappointing outcomes, but they are all one or more releases old, so I figured I'd raise the issue again to see whats going on.

Long story short.

I have one Dell Ultrasharp U3011 (30", 2560x1600) and one Dell Ultrasharp 2007FP  (20", 1600x1200)

When the 2007FP is in landscape mode it matches nearly perfectly in height both pixel and physically wise to the U3011.

See my example picture from my Win 7 dual boot below:

[[img]http://farm6.static.flickr.com/5300/5426195579_da64e6d060_b.jpg[/img]](http://www.flickr.com/photos/mattlach/5426195579/)
[Two Monitors?  Ridiculous...](http://www.flickr.com/photos/mattlach/5426195579/) by [mattlach](http://www.flickr.com/people/mattlach/), on Flickr

The only way I was able to get this to work in Ubuntu was to run two separate X desktops and rotate the 2007FP manually in xorg.conf, and then join them by enabling Xinerama.

Two problems with this solution.

1.) Xinerama is deprecated in favor of Xrandr which I have not been able to make do this.

2.) When using Xinerama Compiz/XGL is disabled, making the desktop feel awfully flat.

Is there any way to avoid this?   Is there any way to rotate just one of your displays and maintain Compiz/XGL functionality?

This is on the top computer in my signature.

Thank you for your help,
Matt

---

### Post by Copper Bezel on 2011-02-11
Did gnome-display-properties not handle things for you? Xrandr is for on-the-fly changes, but you can rotate one display permanently with Gnome Display Properties. Just Preferences - Monitors.

---

### Post by Cracklepop on 2011-02-11
> **mattlach said:**
> ...
1.) Xinerama is deprecated in favor of Xrandr which I have not been able to make do this.

2.) When using Xinerama Compiz/XGL is disabled, making the desktop feel awfully flat.

Is there any way to avoid this?   Is there any way to rotate just one of your displays and maintain Compiz/XGL functionality?

This is on the top computer in my signature.

Thank you for your help,
Matt

1. This doesn't sound right to me... There may a bit of overlap in functionality, but Xinerama is to allow multiple displays/monitors, and xrandr is for changing settings and display properties, etc. 

2. I always thought Xinerama + Compiz couldn't be done, but there seem to be some people who have managed it recently. Maybe...?
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/400566-nvidia-xinerama-compiz-almost-there.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/400566-nvidia-xinerama-compiz-almost-there.html)

---

### Post by mattlach on 2011-02-11
> **Copper Bezel said:**
> Did gnome-display-properties not handle things for you? Xrandr is for on-the-fly changes, but you can rotate one display permanently with Gnome Display Properties. Just Preferences - Monitors.

Gnome Display Properties won't load once the Nvidia drivers are installed.   It offers to load the Nvidia properties app instead, an d it does not have any rotation options.

---

### Post by mattlach on 2011-02-11
> **Cracklepop said:**
> 1. This doesn't sound right to me... There may a bit of overlap in functionality, but Xinerama is to allow multiple displays/monitors, and xrandr is for changing settings and display properties, etc. 

2. I always thought Xinerama + Compiz couldn't be done, but there seem to be some people who have managed it recently. Maybe...?
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/400566-nvidia-xinerama-compiz-almost-there.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/400566-nvidia-xinerama-compiz-almost-there.html)

Hmm.  I'll have to take a look at that.  Maybe it is possible to make Compiz work with Xinerama after all...

---

### Post by Copper Bezel on 2011-02-11
I didn't realize - sorry. Proprietary drivers suck.

Gorgeous setup, by the way. Portrait monitors just don't get nearly enough play, and the matching dimensions are just awesome. = )

---

### Post by mattlach on 2011-02-12
> **Copper Bezel said:**
> I didn't realize - sorry. Proprietary drivers suck.

Gorgeous setup, by the way. Portrait monitors just don't get nearly enough play, and the matching dimensions are just awesome. = )

Thank you. :)   Took some refreshing of my memory of trigonometry to do the math, but I am happy with it.   I was just playing around on eBay not really planning on buying the second monitor, and then, well, I guess I bought it :p

---

### Post by mattlach on 2011-02-21
> **mattlach said:**
> Hmm.  I'll have to take a look at that.  Maybe it is possible to make Compiz work with Xinerama after all...

Looks like I got my answer at your link :(

[quote=Günter]
    Xinerama and Compiz don't work together, full stop. That's why you either have different Xscreens - which means no Xinerama, as the purpose of Xinerama is to make two or more screens into one - or no Compiz if Xinerama works.
    The following applies:
    NVIDIA Twinview and Compiz: OK. But no Xinerama then.
    NVIDIA and Xinerama: OK. But no compositing (Compiz or Kwin) then.
    NVIDIA and two Xscreens and Compiz: OK. But no Xinerama then (ie you can't move Windows between monitors).
    There is no way around the above: believe me, I've tried! You could, of course, use XRandR but not with NVIDIA drivers: not supported (Version 1.2 that is)... [/quote]

---

### Post by KB3MKD on 2011-03-29
I have a slightly different problem. Two monitors both are HP1740, but they rotate in opposite directions. (one CW, the other CCW).
Using Xubuntu, (Xfce) getting the following error message.

"The Resize and Rotate extension (RandR) is not enabled on this display. Try to enable it and run the dialog again."

Right now both of the monitors are rotated the same direction, meaning one of them is upside down.

My xorg.conf file

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP L1740"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP L1740"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RandRRotation" "on"
    Option	   "Rotate" "CW"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
#    Option         "RandRRotation" "on"
#    Option	   "Rotate" "CCW"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1280x1024_60 +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1280x1024_60 +0+1024"
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
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


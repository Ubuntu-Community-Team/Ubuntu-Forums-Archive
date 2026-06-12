---
title: "2 issues"
date: 2005-07-19
forum: Desktop Environments
---

### Post by fimbulvetr on 2005-07-19
Hey all,

I'm having two issues, and was looking for any input on them. I've been using ubuntu for a month or so, and am generally please with it. 

Issue #1: Xinerama. It doesn't work (well). My xorg.conf is extremely simple(see bottom), works in gentoo & redhat and ubuntu refuses to run it properly. Essentially, I boot up with the conf and it doesn't fire up the second monitor. It knows it's there because I can drag apps over there, as well as (guess where the app is) and drag it back to the visible monitor. Here's the strange part:

A. I login, w/o the second LCD working. 
B.I go to system tools -> new login. 
C.I login as myself again and it prompts me with:
"You are already logged in, do you want to continue, switch to your login session, or cancel?"
D. I choose "Switch to login", it brings me back to my locked screen with both LCDs working!

I can't figure it out!

Issue #2:

Whenever I leave my desk area, I always lock my workstation. I do this often during the day. Every once in a while - say every time in 20 - after I return to my session, Xorg is pulling 99%CPU usage with no end in sight. I don't have an strace or anything because it's unbearably slow when it happens and it's not easily replicated.
I use the "Lock Screen" short cut under the gnome menu. Is there a known xscreensave/xorg bug?


Thanks

fim


```
Section "Extensions"
        Option "Composite"      "Enable"
        Option "RENDER"         "Enable"
EndSection

Section "ServerFlags"
  Option "Xinerama" "true"
EndSection

Section "Files"
    RgbPath     "/usr/lib/X11/rgb"
    FontPath    "/usr/share/fonts/local/"
    FontPath    "/usr/share/fonts/misc/"
    FontPath    "/usr/share/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath    "/usr/share/fonts/CID/"
    FontPath    "/usr/share/fonts/Speedo/"
    FontPath    "/usr/share/fonts/75dpi/"
    FontPath    "/usr/share/fonts/100dpi/"
EndSection

Section "Module"
    Load        "dbe"
    SubSection  "extmod"
        Option  "omit xfree86-dga"
    EndSubSection
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load        "dri"
    Load        "GLcore"
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    Driver      "keyboard"
    Option      "AutoRepeat"    "500 5"
EndSection

Section "InputDevice"
    Identifier  "Mouse1"
    Driver      "mouse"
    Option      "Protocol"      "IMPS/2"
    Option      "Device"        "/dev/input/mice"
        Option  "Buttons"       "5"
        Option  "ZAxisMapping"  "4 5"
EndSection

Section "Monitor"
    Identifier  "Generic Monitor"
    HorizSync   30-68
    VertRefresh 50-85
    Option      "DPMS"
EndSection

Section "Device"
    Identifier  "Intel"
    Driver      "i810"
    VendorName  "videocard vendor"
    BoardName   "Intel 865"
    VideoRam    32768
    Option      "DPMS"  "on"
    Option      "RenderAccel"   "on"
EndSection

Section "Device"
        Identifier  "Nvidia"
        Driver      "nv"
        VendorName  "videocard vendor"
        BoardName   "geforcemx"
        VideoRam    32768
        Option      "DPMS"  "on"
        Option      "RenderAccel"   "on"
        BusID      "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Intel"
    Monitor     "Generic Monitor"
    DefaultDepth        24
    SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960"
    EndSubSection
EndSection

Section "Screen"
        Identifier  "Screen 2"
        Device      "Nvidia"
        Monitor     "Generic Monitor"
        DefaultDepth        24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Dual"
        Screen "Screen 2"
        Screen "Screen 1" LeftOf "Screen 2"
        InputDevice "Mouse1" "CorePointer"
        InputDevice "Keyboard1" "CoreKeyboard"
EndSection
```

---

### Post by shakin on 2005-07-19
I don't get it. You've only defined one monitor and set both video cards to use the same monitor. I'm nowhere near an xorg config expert so I could be misreading your config.

I have two monitor sections and bind a video device to each one. Maybe you should try the same thing.

---

### Post by shakin on 2005-07-19
Here, I've added the second monitor section and bound the Intel card to it. Try this config and see what happens.

```

Section "Extensions"
        Option "Composite"      "Enable"
        Option "RENDER"         "Enable"
EndSection

Section "ServerFlags"
  Option "Xinerama" "true"
EndSection

Section "Files"
    RgbPath     "/usr/lib/X11/rgb"
    FontPath    "/usr/share/fonts/local/"
    FontPath    "/usr/share/fonts/misc/"
    FontPath    "/usr/share/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath    "/usr/share/fonts/CID/"
    FontPath    "/usr/share/fonts/Speedo/"
    FontPath    "/usr/share/fonts/75dpi/"
    FontPath    "/usr/share/fonts/100dpi/"
EndSection

Section "Module"
    Load        "dbe"
    SubSection  "extmod"
        Option  "omit xfree86-dga"
    EndSubSection
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load        "dri"
    Load        "GLcore"
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    Driver      "keyboard"
    Option      "AutoRepeat"    "500 5"
EndSection

Section "InputDevice"
    Identifier  "Mouse1"
    Driver      "mouse"
    Option      "Protocol"      "IMPS/2"
    Option      "Device"        "/dev/input/mice"
        Option  "Buttons"       "5"
        Option  "ZAxisMapping"  "4 5"
EndSection

Section "Monitor"
    Identifier  "Generic Monitor"
    HorizSync   30-68
    VertRefresh 50-85
    Option      "DPMS"
EndSection

Section "Monitor"
    Identifier  "Monitor2"
    HorizSync   30-68
    VertRefresh 50-85
    Option      "DPMS"
EndSection

Section "Device"
    Identifier  "Intel"
    Driver      "i810"
    VendorName  "videocard vendor"
    BoardName   "Intel 865"
    VideoRam    32768
    Option      "DPMS"  "on"
    Option      "RenderAccel"   "on"
EndSection

Section "Device"
        Identifier  "Nvidia"
        Driver      "nv"
        VendorName  "videocard vendor"
        BoardName   "geforcemx"
        VideoRam    32768
        Option      "DPMS"  "on"
        Option      "RenderAccel"   "on"
        BusID      "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Intel"
    Monitor     "Monitor2"
    DefaultDepth        24
    SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960"
    EndSubSection
EndSection

Section "Screen"
        Identifier  "Screen 2"
        Device      "Nvidia"
        Monitor     "Generic Monitor"
        DefaultDepth        24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Dual"
        Screen "Screen 2"
        Screen "Screen 1" LeftOf "Screen 2"
        InputDevice "Mouse1" "CorePointer"
        InputDevice "Keyboard1" "CoreKeyboard"
EndSection

```

---

### Post by fimbulvetr on 2005-07-19
They're identical flatpanels - I don't need to identify a different "type" of monitor - only that there are two of the same type.

So "monitor" defines the specs of a certain type of monitor - in my case they are samsung syncmaster 710n. The monitor section is used to define whether to use dpms, what the horiz/vert refreshes are, etc, not that there are two of them.

Screen (n) defines the existence of those monitors. I have two screen sections - one that uses the nvidia device and one that uses the intel device.

Thanks for the reply though...

---

### Post by fimbulvetr on 2005-07-21
Anyone? Please?

---


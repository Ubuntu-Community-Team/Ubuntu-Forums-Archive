---
title: "Odd compiz desktop error"
date: 2008-03-29
forum: Desktop Effects &amp; Customization
---

### Post by 16777216 on 2008-03-29
I have an annoying problem with compiz.
A transparent line the size of my top panel that has some weird behaviour.
Please look at the screen shots to see what I mean.

I had this same issue with compiz-quinnstorm a while ago but I can't remember the solution or find one here in a search.

---

### Post by psyopper on 2008-03-29
Not sure how to help but I have some ideas.

First: What video card are you using? What drivers are you using and what rendering method are you using?

Second: It appears as though you are using a dual monitor system. What dual monitor system are you using - Nvidia Twinview, X, ATI, etc.

Third: It appears as though the graphical issues are on the right monitor. What are the configuration differences between the two monitors? Can you post a copy of your xorg.conf?

---

### Post by 16777216 on 2008-03-29
GeForce 8600
512 MB GT
PCI-E 16x
540 MHz GPU
400 MHz RAM

NVIDIA Driver Version: 169.12

X Screens: 1 TwinView

Placing my panels on the right makes the error move to the left screen.

xorg.conf

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL  M991"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinViewOrientation" "RightOf"
    Option         "Coolbits" "1"
    Option         "NoLogo" "1"
    Option         "RenderAccel" "1"
    Option         "HWCursor" "1"
    Option         "AllowGLXWithComposite" "1"
    Option         "NvAGP" "0"
    Option         "RandRRotation" "0"
    Option         "AllowDDCCI" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "SLI" "0"
    Option         "AIGLX" "1"
    Option         "DamageEvents" "1"
    Option         "UseEvents" "1"
    Option         "TripleBuffer" "1"
##    Option        "DisableGLXRootClipping"    "0"    ## Use it ONLY! if needed!!!
##    Option        "BackingStore"            "0"    ## remove if it screws up
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT-0: 1152x864 +0+0, CRT-1: 1152x864_75 +1152+0; CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0; CRT-0: 1024x768 +0+0, CRT-1: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "DAMAGE" "Enable"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection
```

---

### Post by 16777216 on 2008-04-03
I still have the same problem with no way to get rid of it.

It is as if gnome will not let compiz draw the desk top under the top panel thus shifting it down.

The wallpaper in it's proper position can be seen through the bottom panel and inside of gkrellm. ( Although you can't tell from the included screen shots the theme is transparent and the wall paper is shifted 21 pixels higher than the wallpaper on the rest of my desktop. ) 

Is their a way to delay the starting of the panels or compiz?
Or a way to get compiz to ignore the panels?

---

### Post by 16777216 on 2008-04-04
I finally found a way to fix it.

Tell nautilus to NOT draw the desktop then tell it to draw the desk top again.

Seems to work after logout and reboot.

---

### Post by 22flames on 2008-04-04
nice fix but it seams like the problem was when you add the transparency it blurs and than when you turn on and off and on it than stays without bluring

---

### Post by 16777216 on 2008-04-04
> **22flames said:**
> nice fix but it seams like the problem was when you add the transparency it blurs and than when you turn on and off and on it than stays without bluring

I'm not quite sure what you mean.
The problem was nautilus and compiz fighting over where to draw the desktop. Resulting in a line at the top of head 2 that would not draw correctly, leaving trails of what ever was dragged onto it and not having wallpaper there.
Instead the wallpaper was shifted down on the desktop and shown in it's correct position in the panels and gkrellm.

---

### Post by 22flames on 2008-04-04
ahh ok thanks for clearafing btw cheak your pm

---

### Post by 16777216 on 2008-04-04
Got it

---


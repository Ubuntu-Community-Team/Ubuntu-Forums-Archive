---
title: "Anyone have compiz working with dual head on x600?"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by damrodd on 2007-09-06
Running Fiesty on a Dell GX620 with Radeon X600.  Before compiz, I had dual head working with my two Dell 1907's through VGA.  In order to get compiz to work, I have to use the DVI connection.  Unfortunately, the second screen does not work when using DVI (only a quick, random flicker).  Compiz does work great, but I'd like to use my second screen.  So it appears I need to either make compiz work with VGA or find a way for both monitors to work through DVI.  Compiz will load through VGA, but is unusable as the screen refresh is almost non-existent.  Any ideas?

---

### Post by simontay78 on 2007-09-06
I have a ATI Radeon X600 with Compiz Fusion and it's just a clone when i use DVI and VGA together with dual monitor....

I had previously trying to project my VGA output to a Customized DIY Projector using a OHP (Overhead Projector) so I don't use it for a dual head but a clone...but now my DIY Projector died on me!! :(

My system is 
AMD64 
ATI Radeon X600 256Mb vram
1Gb of DDR Ram 
Ubuntu Feisty 7.04
Compiz Fusion + Emerald

Compiz fusion is great but some bugs here and there...worst is the occasional DHCP problem that dropped my internet connection (within 20min) if I open too many browser tabs or exceed my bandwidth using my Thomson Speedtouch 585v6 Router Wireless modem.

My Macbook don't have issue with my modem...so it's not the modem problem but the Feisty...haiz.

---

### Post by damrodd on 2007-09-11
The problem of not being able to display on both monitors was due to a bad X600 card.  That has been replaced.  However, when I try to start 'gnome with xgl', I get 'fatal server error: no screens found'.  I am able to get xgl to work if I'm only configured for one monitor.  When changing to big desktop, it gets the error message.  Here is my xorg.conf:

[HTML]Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "DELL 1907FP"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "DELL 1907FP"
        DefaultDepth     24
        Option      "AddARGBGLXVisuals" "true"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection[/HTML]

---


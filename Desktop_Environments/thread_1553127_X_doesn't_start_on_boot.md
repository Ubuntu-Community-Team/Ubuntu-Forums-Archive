---
title: "X doesn't start on boot"
date: 2010-08-14
forum: Desktop Environments
---

### Post by x1a4 on 2010-08-14
Hi,

On Xubuntu Hardy, there was a kernel image upgrade recently and since then Xorg doesn't start on boot.  The error I'm getting is: 

Fatal server error: 
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call

I reconfigured the console and reinstalled video drivers (nVidia) but still get the same error.  Currently the only way to start the GUI is to boot to recovery mode, change /etc/X11/xorg.conf to use the generic nVidia driver (nv), reboot.  Then I have to kill GDM, change xorg.conf again to use the the restricted driver (nvidia) and start GDM again.  If I shut down or reboot I get the fatal error and have to redo the above for everything to work.  Using a minimalist xorg.conf doesn't help. 

I'm using the 2.6.24-28-generic kernel and nVidia drivers (ver. 173.14.25) from the nVidia site.  Using drivers from the repositories produces the same result.  Reconfiguring the xserver using dpkg doesn't help either.  

My xorg.conf file: 
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Gyration Compact Keyboard"
    InputDevice    "MS Mouse"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "glx"
    Load           "dbe"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
  # Load    "type1"
    Load           "vbe"
    Load           "v4l"
    Load           "shadow"
EndSection

Section "InputDevice"
    Identifier     "Gyration Compact Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:lwin_switch,compose:rwin"
EndSection

Section "InputDevice"
    Identifier     "MS Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Sceptre"
    VendorName     "Sceptre, Inc."
    ModelName      "Sceptre X5S-Naga"
    DisplaySize     270    203
    HorizSync       24.0 - 62.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -hsync +vsync
    ModeLine       "1024x768_66.00" 71.63 1024 1080 1192 1360 768 769 772 798 -hsync +vsync
    ModeLine       "1024x768_70.00" 76.16 1024 1080 1192 1360 768 769 772 800 -hsync +vsync
    ModeLine       "1024x768_72.00" 78.43 1024 1080 1192 1360 768 769 772 801 -hsync +vsync
    ModeLine       "1024x768_75.00" 81.80 1024 1080 1192 1360 768 769 772 802 -hsync +vsync
    ModeLine       "800x600_60.00" 38.22 800 832 912 1024 600 601 604 622 -hsync +vsync
    ModeLine       "800x600_66.00" 42.83 800 840 920 1040 600 601 604 624 -hsync +vsync
    ModeLine       "800x600_70.00" 45.50 800 840 920 1040 600 601 604 625 -hsync +vsync
    ModeLine       "800x600_72.00" 46.87 800 840 920 1040 600 601 604 626 -hsync +vsync
    ModeLine       "800x600_75.00" 48.91 800 840 920 1040 600 601 604 627 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "MSI GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia"
    Monitor        "Sceptre"
    DefaultDepth    24
    Option         "NvAGP" "3"
    Option         "Accel" "on"
    Option         "RenderAccel" "on"
    Option         "AccelMethod" "XAA"
    Option         "AllowGLXWithComposite" "on"
    Option         "XAANoOffscreenPixmaps" "on"
    Option         "DigitalVibrance" "3"
    Option         "ImageSharpening" "3"
    Option         "Overlay" "off"
    Option         "CIOverlay" "on"
    Option         "TransparentIndex" "0"
    Option         "OverlayDefaultVisual" "off"
    Option         "SWCursor" "off"
    Option         "HWCursor" "on"
    Option         "CursorShadow" "off"
    Option         "CursorShadowAlpha" "64"
    Option         "CursorShadowXOffset" "4"
    Option         "CursorShadowYOffset" "2"
    Option         "Coolbits" "1"
    Option         "TwinView" "0"
    Option         "NoLogo" "True"
    Option         "UseEdidDpi" "false"
    Option         "DPI" "96 x 96"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_72" "1024x768_70" "1024x768_66" "1024x768_60" "1024x768" "800x600_72" "800x600_66" "800x600_60" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```


Any ideas?

Thank you.

---

### Post by x1a4 on 2010-08-26
*bump* 

There have been two more kernel image updates since this began happening (last one today) and each time I hoped things would start working again but they didn't.

---


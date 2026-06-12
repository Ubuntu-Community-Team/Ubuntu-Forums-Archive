---
title: "ATI tv-out: TV display is corrupt"
date: 2006-03-04
forum: Desktop Environments
---

### Post by DrSkalpell on 2006-03-04
I have installed ATI-drivers, and everything is ok except for one thing: Tv-out does not work properly. Attached is a picture of the tv sceen. It seems to be the same problem which is adressed in the ATI Proprietary Linux release notes:

[I]TV Display is Corrupt After Switching Resolutions

This information applies to the following system configurations:

    * ATI Proprietary Linux Driver 3.7.1 and later
    * TV Out enabled in aticonfig
    * Big Desktop or Dual Head monitor layout is used 

This issue does not occur in Clone Mode or when the TV is the only connected display.

Upon using the resolution keyboard shortcuts (ctrl-alt-+) or (ctrl-alt--) to switch resolution of the XFree86 Desktop, the display will be off center or completely corrupt.

The TV display is not usable in this state and it is not possible to get back to a stable resolution once this has happened. A restart is required. [/I]

Are there anybody out there who has experienced the same problem and/or know how to fix this?

Attached is also my xorg.conf file.

---

### Post by DrSkalpell on 2006-04-02
SOLVED:

1. Changed to clone mode:

Option "DesktopSetup"               "Clone" 

2. To be able to view video on the tv:

Option "OverlayOnCRTC2"		"on" 

TV out is now working :-D 

Here is my xorg.conf file:

[I]Section "dri"
    Mode 0666
EndSection

Section "Module"
   Load        "dbe"  	
      
   SubSection  "extmod"
      Option   "omit xfree86-dga"   
   EndSubSection

   Load        "type1"
   Load        "freetype"
   Load        "glx"   # libglx.a
   Load        "dri"   # libdri.a
EndSection

Section "Files"
    RgbPath	"/usr/X11R6/lib/X11/rgb"
    
    FontPath	"/usr/share/X11/fonts/misc"
    FontPath	"/usr/share/X11/fonts/cyrillic"
    FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath	"/usr/share/X11/fonts/Type1"
    FontPath	"/usr/share/X11/fonts/CID"
    FontPath	"/usr/share/X11/fonts/100dpi"
    FontPath	"/usr/share/X11/fonts/75dpi"
    # paths to defoma fonts
    FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "ServerFlags"
EndSection

Section "InputDevice"
    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"no"
EndSection

Section "InputDevice"
    Identifier	"Mouse1"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ImPS/2"
    Option "Emulate3Buttons" "true"
    Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier  "Monitor0"
EndSection

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"
    Driver      "vga"
EndSection

Section "Device"
   Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" 
    Option "DesktopSetup"               "Clone" 
    Option "ScreenOverlap"              "0" 
    Option "TVFormat"                   "PAL-B"     
    Option "TVStandard"                 "VIDEO"
    Option "OverlayOnCRTC2"		"on"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
    Option "CenterMode"                 "off"
    Option "PseudoColorVisuals"         "off"
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1680x1050" "1024x768" "800x600" "640x480"
        ViewPort    0 0  
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "Server Layout"
    Screen "Screen0"
    InputDevice "Mouse1"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection[/I]

---

### Post by nalmeth on 2006-04-02
Are you using the ATITVOUT package? Or is this just the ATI driver allowing you to go TV out? 
I've got TV out on my laptop, but can't get anything to show up.

---


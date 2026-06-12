---
title: "FGLRX, XGL No Mouse, Keyboard"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by catfishk on 2007-07-08
i have been through the various install docs a few times each, but when switching to XGL via the GDM login screen, i get no mouse or keyboard feedback immediately following the gnome splash.  just a 'frozen' gnome-session displaying my background image and toolbars.  if i right click and create folder, though i cannot see it, the folder will be there when i CTRL+ALT+BACKSPACE and login to a standard gnome-session

 it appears it is a problem with XGL on display :1?

 Lenovo Thinkpad T60 Ubuntu Feisty Fawn
 ATI X1300 fglrx proprietary drivers ver 8.38.6

**/etc/X11/xorg.conf:**

 Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "GLcore"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
        Option      "EmulateWheel" "on"
        Option      "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "SHMConfig" "1"
EndSection

Section "Monitor"
        Identifier   "IBM Internal Display"
        Option      "DPMS"
EndSection

Section "Device"
#       Driver      "vesa"
#       Option      "DisableGLXRootClipping" "True"
#       Option      "SubPixelOrder"     "NONE"
#       Option      "DesktopSetup" "horizontal" #Enable Big Desktop
        Identifier  "ATI Technologies, Inc. Radeon X1300 (M52 7149)"
        Driver      "fglrx"
#       Driver      "radeon"
#       Option      "KernelModuleParm" "agplock=0"
        Option      "backingstore" "true"
        Option      "AGPMode" "4"
        Option      "AddARGBGLXVisuals" "true"
        Option      "DisableGLXRootClipping" "true"
        Option      "AGPFastWrite" "true"
#       Option      "no_accel" "no"
#       Option      "no_dri" "no"
#       Option      "Stereo" "off"
#       Option      "StereoSyncEnable" "1"
#       Option      "DynamicClocks" "on"
#       Option      "mtrr" "on"
#       Option      "DesktopSetup" "Single"
#       Option      "ScreenOverlap" "0"
#       Option      "Capabilities" "0x00000000"
#       Option      "CapabilitiesEx" "0x00000000"
#       Option      "VideoOverlay" "on"
#       Option      "OpenGLOverlay" "off"
#       Option      "CenterMode" "off"
#       Option      "PseudoColorVisuals" "off"
        Option      "EnablePageFlip" "true"
        Option      "AllowGLXWithComposite" "true"
        Option      "RenderAccel" "true"
#       Option          "XAANoOffscreenPixmaps" "true"
        Option      "AccelMethode" "EXA"
#       Option          "NoDDC"
        Option      "DynamicClocks" "on"
        Option      "bioshotkeys" "true"
        Option      "UseInternalAGPGART" "no"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "Mode2" "1280x1024"         #Resolution for second monitor
        Option      "DesktopSetup" "LVDS,AUTO"  #LVDS = LCD, CRT, AUTO
        Option      "EnablePrivateBackZ" "yes"  #Enable 3D; may not work!
        Option      "HSync2" "65"
        Option      "VRefresh2" "60"
        Option      "Centermode" "off"
        Option      "PseudoColorVisuals" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon X1300 (M52 7149)"
        Monitor    "IBM Internal Display"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"

#               Modes    "1024x768"
                Depth     24
                Modes    "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

Section "ServerFlags"
        Option "AIGLX" "off"
EndSection

**/usr/bin/startxgl:**

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
sleep 4
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

**/usr/share/xsessions/xgl.desktop:**

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Gnome with Xgl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

---

### Post by catfishk on 2007-11-28
UPDATE: all this was fixed when the new AMD/ATI fglrx driver version 8.43.2 was installed, which uses AIGLX and not XGL

---


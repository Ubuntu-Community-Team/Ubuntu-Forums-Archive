---
title: "View_On_Tv ( X error, nvidia driver )"
date: 2006-09-13
forum: Desktop Environments
---

### Post by kaitlyn on 2006-09-13
Hello,

Along the path to making View_On_Tv work, I've run into another issue.  After getting X to be able to be run by nonroot users, this happens when I try to start the X server on my tv:

```

kaitlyn@medea:~$ X -screen TV -ac :2
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux medea 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:0                0 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Wed Sep 13 20:32:56 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) NVIDIA(0): Failure reading maximum pixel clock value for display device
(EE) NVIDIA(0):     TV-0.
(EE) NVIDIA(0): The requested configuration of display devices is not
(EE) NVIDIA(0):     supported in the hardware.

Fatal server error:
AddScreen/ScreenInit failed for driver 0


   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: X(AbortServer+0x23) [0x819c51a]
3: X(FatalError+0x66) [0x819c7cc]
4: X(InitOutput+0xe5a) [0x809e89a]
5: X(main+0x292) [0x806deee]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d88ea2]
7: X(FontFileCompleteXLFD+0x85) [0x806d641]

FatalError re-entered, aborting
Caught signal 11.  Server aborting

```


My xorg.conf file is:
```

# /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier  "Main Layout"
    Screen      0       "Screen0" 0 0
    InputDevice "Mouse0" "CorePointer"
    InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
        #Server Flags.
EndSection

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
    SubSection  "extmod"
        Option  "omit xfree86-dga"
    EndSubSection
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "keyboard"
    Option      "AutoRepeat"    "150 100" # LTK= 10 500 ETK= 500 5
EndSection

# External Mouse
#Section "InputDevice"
#    Identifier  "Mouse0" 
#    Driver      "mouse"
#    Option "Protocol"     "auto"
#    Option "Device"       "/dev/input/mice"
#    Option "ZAxisMapping" "4 5" 
#    Option "Buttons"      "7"
#EndSection
Section "InputDevice"
Driver        "synaptics"
Identifier    "Mouse0"
Option        "Device"               "/dev/psaux"
Option        "Protocol"              "auto-dev"
   #Option        "LeftEdge"              "120"
   #Option        "RightEdge"             "830"
   #Option        "TopEdge"               "120"
   #Option        "BottomEdge"            "650"
   #Option        "FingerLow"             "14"
   #Option        "FingerHigh"            "15"
Option        "MaxTapTime"            "0"
Option        "MaxTapMove"            "110"
Option        "EmulateMidButtonTime"  "75"
Option        "VertScrollDelta"       "20"
Option        "HorizScrollDelta"      "0"
Option        "MinSpeed"              "0.3"   #Real Value 0.3
Option        "MaxSpeed"              "0.15"  #Real Value 0.75
Option        "AccelFactor"           "0.005" #real Value 0.015
Option        "EdgeMotionMinSpeed"    "200"
Option        "EdgeMotionMaxSpeed"    "200"
Option        "UpDownScrolling"       "1"
Option        "CircularScrolling"     "1"
Option        "CircScrollDelta"       "0.1"
Option        "CircScrollTrigger"     "2"
EndSection

Section "Monitor"
Identifier "Toshiba"
HorizSync 75
VertRefresh 60
Modeline "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 -HSync -Vsync

EndSection

Section "Device"
Identifier "NVIDIA Corporation NV17 [GeForce4 440 Go]"
Driver "nvidia" # nvidia
VideoRam 65536
Option "IgnoreEDID" "true"
Option "NoLogo" "true"
Option "PowerSaverHsyncOn"
Option "Mobile" "2"
Option "NoBandWidthTest"
Option "RenderAccel" "On" 
Option "NvAGP" "3"  
Option "AllowGLXWithComposite" "true" 
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "NVIDIA Corporation NV17 [GeForce4 440 Go]"
    Monitor     "Toshiba"
    DefaultDepth 16
    SubSection "Display"
        Depth           24
        Modes           "1600x1200"
        ViewPort        0 0
        Virtual         1600 1200
    EndSubsection
    # From the install manual.
    # Option         "ExactModeTimingsDVI"   "TRUE"
    # Option         "ModeValidation"   "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    # Might use:
     Option "ExactModeTimingsDVI"
     Option "UseEdidDpi" "FALSE"
     Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
    
     # Encryptio
    Option "ModeValidation" "NoMaxPClkCheck"
EndSection


########################
#######################         This Area is for TV to work!
#####################

Section "Monitor"
        Identifier      "TV-monitor"
        VendorName      "Sanyo"
        ModelName       "Television"
        Option          "ConnectedMonitor" "TV"
        HorizSync       30-50
        VertRefresh     60
        Option          "dpms"
EndSection 

Section "Device"
        Identifier      "TV-device"
        Driver          "nvidia"
        VendorName      "Monitor Vendor"
        BoardName       "NVIDIA Corporation NV17 [GeForce4 440 Go]"
        Option          "NoLogo" "true"
        Option          "NvAGP" "2"
        Option          "RenderAccel" "On"
        Option          "AllowGLXWithComposite" "true"
        Screen          0
        Option          "TVStandard" "NTSC-M"
        Option          "TVOutFormat" "COMPOSITE"    # (or "SVIDEO" if that's what you're using)
        Option          "ConnectedMonitor" "TV"
    
        # Encryptio
        Option "ModeValidation" "NoMaxPClkCheck"

        # Option "IgnoreEDID" "true"
        # Option "ExactModeTimingsDVI"
        # Option "UseEdidDpi" "FALSE"
        # Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"

EndSection

Section "Screen"
        Identifier   "TV"
        Device       "TV-device"
        Monitor      "TV-monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes     "800x600"
        EndSubSection
EndSection 

```

I have no idea what to do about this.  Following a friends idea, I added the following to /etc/modprobe.conf.local

```

option nvidia NVreg_SoftEDIDs=0 NVreg_
option nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4

```

But, no luck.

Any ideas would be very much appreciated.

---


---
title: "Wacom tablet does not work in Dapper"
date: 2007-08-18
forum: Desktop Environments
---

### Post by obender on 2007-08-18
I tried to move my Wacom Graphire tablet fom my windows pc to my linux box but I can not get it to work.
wacdump shows activity and if I set the DebugLevel to 10 in xorg.conf I can see in the log entries like this when I move the stylus above the tablet:

```
commonDispatchEvents
xf86WcmEvent: c=0 i=2 t=0 s=0 x=5245 y=6426 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=2036737210
xf86WcmEvent: c=0 i=2 t=0 s=0 x=5230 y=6570 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=2036737218
```

Here's a chunk from the xorg log just before the above events:

```
BEGIN xf86WcmProc dev=0x872080 priv=0x871da0 type=eraser flags=20 what=2
xf86WcmProc pWcm=0x872080 what=OFF
Wacom number of open devices = 3
END xf86WcmProc Success what=2 dev=0x872080 priv=0x871da0
BEGIN xf86WcmProc dev=0x872290 priv=0x8715b0 type=cursor flags=2 what=2
xf86WcmProc pWcm=0x872290 what=OFF
Wacom number of open devices = 2
END xf86WcmProc Success what=2 dev=0x872290 priv=0x8715b0
BEGIN xf86WcmProc dev=0x8724c0 priv=0x870510 type=stylus flags=17 what=2
xf86WcmProc pWcm=0x8724c0 what=OFF
Wacom number of open devices = 1
Closing device; uninitializing.
END xf86WcmProc Success what=2 dev=0x8724c0 priv=0x870510
(II) Configured Mouse-usb-0000:00:02.0-1/input0: Off
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
BEGIN xf86WcmProc dev=0x872080 priv=0x871da0 type=eraser flags=20 what=1
xf86WcmProc fd=-1 pWcm=0x872080 what=ON
xf86WcmInitDevice: opening /dev/input/wacom
(**) Option "Device" "/dev/input/wacom"
usbDetect
eraser Wacom X driver grabbed event device
initializing USB tablet
detected a protocol 4 model (Wacom Graphire)
(==) Wacom USB Graphire tablet speed=9600 maxX=10206 maxY=7422 maxZ=511 resX=2032 resY=2032 suppress=2 tilt=disabled
Marking all devices open
END xf86WcmProc Success what=1 dev=0x872080 priv=0x871da0
BEGIN xf86WcmProc dev=0x872290 priv=0x8715b0 type=cursor flags=2 what=1
xf86WcmProc fd=14 pWcm=0x872290 what=ON
END xf86WcmProc Success what=1 dev=0x872290 priv=0x8715b0
BEGIN xf86WcmProc dev=0x8724c0 priv=0x870510 type=stylus flags=17 what=1
xf86WcmProc fd=14 pWcm=0x8724c0 what=ON
END xf86WcmProc Success what=1 dev=0x8724c0 priv=0x870510
(II) Configured Mouse-usb-0000:00:02.0-1/input0: On
(II) evdev brain: Rescanning devices (3).
```


If I run xidump "stylus" it does not show any activity and apart from generating lines in the log the styIus does not have any effect. 

I am running ubuntu dapper with a vanilla kernel 2.6.20.

Here's the xorg.conf content:
```
Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc101"
    Option         "XkbLayout" "ro"
    Option         "XkbVariant" "comma"
    Option         "XkbOptions" "ctrl:nocaps"
EndSection

#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
#    Option         "ZAxisMapping" "4 5"
#    Option         "Emulate3Buttons" "false"
#EndSection

Section "InputDevice"
    Identifier      "Configured Mouse"
    Option          "CorePointer"
    Driver          "evdev"
    Option          "Protocol" "evdev"
#    Option          "Dev Name" "Logitech USB-PS/2 Optical Mouse" 
    Option          "Dev Phys" "usb-*/input0"
#    Option          "Dev Phys" "usb-0000:00:02.0-1/input0"
    Option          "Device" "/dev/input/event1"
#    Option          "Buttons" "9"
#    Option          "ZAxisMapping" "4 5 7 6"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "Mode" "Absolute"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
    Option         "USB" "on"               		# USB ONLY
    Option         "DebugLevel" "10"
    Option         "SendCoreEvents" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "Mode" "Absolute"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
    Option         "USB" "on"               		# USB ONLY
    Option         "SendCoreEvents" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
    Option         "USB" "on"               		# USB ONLY
    Option         "SendCoreEvents" "true"
EndSection

Section "Monitor"
    Identifier     "SyncMaster1"
    Option         "DPMS"
    HorizSync      30.0.-81.0
    VertRefresh    60-60
EndSection

Section "Monitor"
    Identifier     "SyncMaster2"
    Option         "DPMS"
    HorizSync      30-81
    VertRefresh    60-60
EndSection

Section "Monitor"
    Identifier     "TwinMoni"
    Option         "DPMS"
    HorizSync      30-81
    VertRefresh    60-60
    DisplaySize    675 270
EndSection

#################

Section "Device"
    Identifier "NvidiaTwin"
    Driver "nvidia"
    BusID "PCI:5:0:0"
    Option "NoLogo" "0"
    Option "TwinView"
    Option "MetaModes"  "1280x1024,1280x1024; 1280x1024; 1024x768,1024x768; 1024x768; 800x600,800x600; 800x600"
    Option "TwinViewOrientation" "CRT-1 RightOf CRT-0"
    Option "HorizSync"   "CRT-0: 30-81; CRT-1: 30-81"
    Option "VertRefresh" "CRT-0: 60-60; CRT-1: 60-60"
    Option "ConnectedMonitor" "CRT-0,CRT-1"
    Option "RenderAccel" "False"
    Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "FALSE"
    Option "CursorShadow" "1"
EndSection

Section "Screen"
    Identifier	"ScreenTwin"
    Device      "NvidiaTwin"
    Monitor	"TwinMoni"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier	    "twinview"
    Screen	    0 "ScreenTwin"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option "Xinerama" "0"
EndSection

##############
```

Could someone please help, I am losing hope on this one.
Thanks

---

### Post by obender on 2007-08-18
I recompiled wacom_drv.so with linuxwacom-0.7.8-3 from sourceforge and now Xorg can see the tablet.

Still has some rough corners, I can only click with the eraser end.

---


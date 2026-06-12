---
title: "Resolution Problems"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by aetherh4cker on 2007-07-20
I want the 1600x1024 resolution. I'm 100% both my monitor and video card support it. However, it's not an option in System > Preferences > Screen Resolution.

I use the 1600x1024 on windows and would like help getting it on here!

I went through all the installation procedures for the nVidia drivers, and it seemed to work, but I don't see the nVidia grey screen on startup.

I read that I should go into Restricted Drivers Manager, but it says this:
You need to install the package

  linux-restricted-modules-2.6.20-16-server

for this program to work.

Help!

---

### Post by dougfractal on 2007-07-20
in terminal
```
sudo apt-get install linux-restricted-modules-2.6.20-16-server
```

does the command
```
grep "nvidia" /etc/X11/xorg.conf
```

give  > Driver         "nvidia"

if not ```
sudo apt-get nvidia-glx-new
```
or "sudo apt-get nvidia-glx" depending on the card

I'm surprised that Restricted Drivers Manager doesn't work may be because it's server edition. File a bug on launchpad

---

### Post by aetherh4cker on 2007-07-20
nick@hina:~$ sudo apt-get install linux-restricted-modules-2.6.20-16-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.20-16-server
nick@hina:~$

Edit:  And grep "nvidia" /etc/X11/xorg.conf does indeed return Driver "nvidia".

---

### Post by dougfractal on 2007-07-20
I found this [http://ubuntuforums.org/showthread.php?t=480659](http://ubuntuforums.org/showthread.php?t=480659)
it looks like you will need to install linux-image-generic along with linux-restricted-modules-generic

but "cat /var/log/Xorg.0.log"
referes to NVIDIA or nv?

If nvidia is working then the res should'nt be a problem

uname -r      # check kernel version

in Section "Device"
Option "NoLogo" "false"     # display splash

---

### Post by aetherh4cker on 2007-07-20
cat /var/log/Xorg.0.log (only copied bottom third)
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "false"
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.05.51
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     CMO CMC 22 W (DFP-0)
(--) NVIDIA(0): CMO CMC 22 W (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): CMO CMC 22 W (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (55, 65); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xfc000000 - 0xfcffffff (0x1000000) MX[B]
        [1] 0   0       0xc0000000 - 0xcfffffff (0x10000000) MX[B]
        [2] 0   0       0xfd000000 - 0xfdffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
        [8] -1  0       0xfeafe000 - 0xfeafe7ff (0x800) MX[B]
        [9] -1  0       0xfeafec00 - 0xfeafecff (0x100) MX[B]
        [10] -1 0       0xfeaff000 - 0xfeafffff (0x1000) MX[B]
        [11] -1 0       0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
        [12] -1 0       0x50000000 - 0x500003ff (0x400) MX[B]
        [13] -1 0       0xfebffc00 - 0xfebfffff (0x400) MX[B]
        [14] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [15] -1 0       0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
        [16] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [17] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [18] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [19] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [20] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [21] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [23] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [24] -1 0       0x0000bc00 - 0x0000bc07 (0x8) IX[B]
        [25] -1 0       0x0000ac00 - 0x0000ac3f (0x40) IX[B]
        [26] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [27] -1 0       0x0000b400 - 0x0000b407 (0x8) IX[B]
        [28] -1 0       0x0000b800 - 0x0000b807 (0x8) IX[B]
        [29] -1 0       0x00009c00 - 0x00009c1f (0x20) IX[B]
        [30] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [31] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [32] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [33] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [34] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [35] -1 0       0x0000ec00 - 0x0000ec07 (0x8) IX[B]
        [36] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [37] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [38] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [39] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [40] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [41] -1 0       0x0000d800 - 0x0000d81f (0x20) IX[B]
        [42] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [43] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [44] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[B]
        [45] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [46] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetClientVersion: 0 9
nick@hina:~$ 
```

And here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
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
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "NoLogo" "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

uname -r:
```
2.6.20-16-server
```

I added your NoLogo and I still don't see the logo...

The driver seems to be working... I think... but my resolution I know is supported isn't an option in System > Preferences > Screen Resolution.

---

### Post by dougfractal on 2007-07-21
Well you've certainly have nvidia.  ;-)

Your moniter hasn't been dectected, so find the right values and add them to the conf
```

Section "Monitor"
    Identifier     "Monitor"   # "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection
```


I've added some more screen modes, but until the moniter values  are correct they wont work.
```

Section "Device" 
    Identifier     "Nvidia GeForce 6200"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:1:0:0"
    Driver         "nvidia"
    Option         "NoLogo" "false"
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia GeForce 6200"
    Monitor        "Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
 SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by aetherh4cker on 2007-07-21
> **dougfractal said:**
> Well you've certainly have nvidia.  ;-)

Your moniter hasn't been dectected, so find the right values and add them to the conf

What do you mean by 'find the right values'?  I have no idea how to go about doing that.

I have a CHIMEI CMV 221D monitor, 22in widescreen.

Also, thanks a ton for your help so far.

---

### Post by dougfractal on 2007-07-22
Try the DELL 2007WFP values
As this isn't your monitor's manufacturer it could not work and may damage your hardware, I take no responsibility for your choice to use it.

But i think it will be fine.  

```
Section "Monitor"
    Identifier     "DELL 2007WFP"   #  CHIMEI CMV 221D monitor, 22in
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device" 
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    VendorName     "NVIDIA Corporation"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DELL 2007WFP"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"


    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by aetherh4cker on 2007-07-23
What is?:
HorizSync 28.0 - 51.0
VertRefresh 43.0 - 60.0

What do these two do?  How do I find what to set them at?  I've found this info about my monitor:

CMV 221D

Pixel Pitch: 0.282 mm
Resolution: 1,680*1,050 WSXGA+
Display Color: 16.7 M (8 bits Hi-FRC)
Brightness: 330 cd/m2
Contrast Ratio: 800:1
Viewing Angle
Viewing Angle (Horizontal): 170°
Viewing Angle (Vertical): 160°
Scan Rate (Horizontal): 30 kHz ~ 82 kHz
Scan Rate (Vertical): 56 Hz ~ 76 Hz
Display Area: 474 mm x 296 mm
Response time: 5 ms

532 mm (W) x 402 mm (H) x 224 mm (D)

Digital Interface: DVI-D
Analog Interface: D-Sub

Power Source: 100~240VAC, 50/60 Hz
Weight: 4.5 kg&#65117;Including Stand&#65118;
Tilt Angle: 0° ~ 20°
Wall Mount: VESA Standard
Power Consumption: 48 W (max)
Power Saving State: 2 W (max)
Function: Kensington (Anti-theft Lock)
Color: Silver-Black

---

### Post by dougfractal on 2007-07-24
> **aetherh4cker said:**
> What is?:
HorizSync 28.0 - 51.0
VertRefresh 43.0 - 60.0

What do these two do?  
Generic monitor values

> **aetherh4cker said:**
> 
How do I find what to set them at?  I've found this info about my monitor:

CMV 221D

Scan Rate (Horizontal): 30 kHz ~ 82 kHz
Scan Rate (Vertical): 56 Hz ~ 76 Hz



so replace in the xorg.conf: Section "Monitor"
```

Section "Monitor"
    Identifier     "CHIMEI CMV 221D"   
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

```
(look like the Dell values would have worked as well [img]http://ubuntuforums.org/images/icons/icon10.gif[/img] )

replace  the section "screen"
  ```

    Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "CHIMEI CMV 221D"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection








```


Thanks for giving good hardware info.

---

### Post by aetherh4cker on 2007-07-24
Made your changes and it crashed on startup.

I'm no pro (not even an novice yet...), but reading through the output, it seems like it didn't like this line in the Screen section:

Device         "NVIDIA Corporation NVIDIA Default Card"

So I changed it to match what my other stuff was set at:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "NoLogo" "false"
EndSection


So I changed the screen section  to say:

Device         "Generic Video Card"

... and things seem to be working fine with all your values...

Booted up in my preffered resolution.  Do I want to change anything else?  Maybe my "Device" section?

... and man, I really appreciate you helping me with this.  The private message asking if I got things sorted out was really cool.  This linux experience is going much better than my last (Fedora Core).

Thanks dood.

---


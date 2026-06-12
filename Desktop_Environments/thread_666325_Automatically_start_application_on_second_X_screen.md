---
title: "Automatically start application on second X screen"
date: 2008-01-13
forum: Desktop Environments
---

### Post by justinleewilson on 2008-01-13
Hey,

I've setup a mythtv system which has both my standard monitor and a tv setup to run in different X screens (did this using nvidia-settings). There is an admin app which comes with the mythbuntu distro called Mythbuntu Control Center which allows me to automatically run the frontend for mythtv at startup so that it works just like a set to box. 

The problem is that the fronted is appearing on my monitor (default X screen) and not my tv (secondary X screen). 

The system automatically boots into xfce so I guess it has something to do with this environment.

Could anybody help please, I'm tearing my hair out :-)

Thanks in advance,

Justin

I'v attached my xorg.conf to give a better understanding of my setup:

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
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
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "EV985TCO99"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Taxan EV985TCO99"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 180.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    #HorizSync       28.0 - 33.0
    #VertRefresh     43.0 - 72.0
    HorizSync 30-50
    VertRefresh 60 
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7300 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:3:0:0"
    Screen          1
    Option         "TVOutFormat" "S-VIDEO" #or COMPOSITE etc
    Option         "TVStandard" "PAL-G" #or NTSC etc
    Option          "ConnectedMonitor" "Monitor1" 
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7300 GT]"
    Monitor        "EV985TCO99"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0; CRT: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 640x480 +0+0"
EndSection

---

### Post by Subban on 2008-01-13
I think you will need to use Devils Pie, it allows you to define which monitor an application will appear on when it starts and other neat things.

I dont' think there is any other way, that I've seen.

---

### Post by justinleewilson on 2008-01-13
Hi,

Thanks for the quick reply, I'll check it out... cheers :-)

Justin

---

### Post by justinleewilson on 2008-01-13
Hi again,

I've just checked the devils pie documentation and unfortunately I don't think it covers my needs. With devils pie you can set the default workspace for an application within an x screen, you can't set the actual x screen itself :-(

Does anybody else have any other suggestions, I'm sure this sort of thing must've been done before :-)

Cheers,

Justin

---


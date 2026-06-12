---
title: "No panels or desktop menu on 3rd screen?"
date: 2009-08-13
forum: Desktop Environments
---

### Post by bheyes on 2009-08-13
Hello everyone,

I don't have any Gnome panels appearing on my 3rd screen.

The desktop image is being displayed correctly and I can use the screen by sending a window directly to it (e.g. export DISPLAY=:0.2; firefox &) but when I try to right click on the desktop there is no menu.

I'm not loading any special modules or extensions.

Am I missing something?

Any help would be much appreciated.

Thanks,

-Brent


Screen configuration:

screen 0: laptop 
screen 1: laptop external VGA
screen 2: displaylink external USB

xorg.conf:

```


Section "ServerLayout"
    Identifier     "Server Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    ModulePath      "/usr/local/lib/xorg/modules"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

## Screen 0 ##

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
    Screen	   0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes       "1280x800"
    EndSubSection
EndSection

## Screen 1 ##

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
    Screen	   1
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes       "1680x1059"
    EndSubSection
EndSection

## Screen 2 ##

Section "Device"
        Identifier      "Device2"
        driver          "displaylink"
        Option  	"fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "Monitor2"
EndSection

Section "Screen"
        Identifier      "Screen2"
	Device          "Device2"
        Monitor         "Monitor2"
        SubSection "Display"
                Depth   24
		Modes   "1440x900"
        EndSubSection
EndSection


```

---

### Post by themrcul on 2009-10-30
I have this same issue as well, if anyone knows a solution please tell us :)

---

### Post by talthing on 2011-04-24
I can`t seem to get my Displaylink monitor configured.
I do see the green screen but I can`t seem to get past that.

I`m hoping someone can show me where I went wrong

system IBM x40    distro 10.04    monitor Dell 2007FP

Here is what I`ve compiled in my attempts to troubleshoot the problem

$ uname -r
    2.6.34-020634-generic

$ ls /dev/fb*
    /dev/fb0  /dev/fb1

$ dmesg | grep usb
[    0.319628] usbcore: registered new interface driver usbfs
[    0.319656] usbcore: registered new interface driver hub
[    0.319706] usbcore: registered new device driver usb
[    1.983679] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   10.020356] usb 1-3: dlfb: allocated 4 65024 byte urbs 
[   10.178499] usb 1-3: dlfb: set_par mode 1600x1200
[   10.323648] usb 1-3: dlfb: DisplayLink USB device /dev/fb1 attached. 1600x1200 resolution. Using 7500K framebuffer memory
[   10.324873] usbcore: registered new interface driver udlfb

$ sudo apt-get -y install libusb-dev xorg-dev xserver-xorg-video-displaylink  git-core
    libusb-dev is already the newest version.
    xorg-dev is already the newest version.
    xserver-xorg-video-displaylink is already the newest version.
    git-core is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo ./test1    #libdlo test senario
   (test runs a series of shapes and colors ending with `DisplayLink` logo     in multiple positions on the monitor as expected)

$ gedit xorg.conf (pertaining info)
Section "ServerLayout"
            Identifier     "Layout0"
            Screen      0  "Screen0"
            Screen      1  "Screen1" RightOf "Screen0"
            Screen      2  "DisplayLinkScreen" RightOf "Screen1"
            InputDevice    "Keyboard0" "CoreKeyboard"
            InputDevice    "Mouse0" "CorePointer"
        EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
            ModulePath   "/usr/local/lib"
    EndSection    

Section "Monitor"
        Identifier   "Monitor2"
            VendorName     "DELL"
            ModelName      "DELL 2007FP"
            HorizSync       31.0 - 83.0
            VertRefresh     56.0 - 76.0
       EndSection

    #DisplayLinkScreen#                                                                  

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
        Identifier     "DisplayLinkMonitor"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
            #Virtual     1280 1024
                Depth   24
        Modes   "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

---


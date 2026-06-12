---
title: "No compiz on gutsy with xinerama - 'RenderBadPicture (invalid Picture parameter)'"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by jubalj on 2007-10-09
Hi guys,

I cant get compiz to load on gutsy beta (compiz 1:0.6.0+git20071006-0ubuntu2), i'm running xinerama (1920x1440,2580x1800) on a nvidia 7950GX2.

i'm initally getting this error ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141543](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141543))
> jubalj@jub0:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0294 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (4480x1600) to maximum 3D texture size (4096): Failed.
aborting and using fallback: /usr/bin/metacity 

so I've tried to get past it using 'SKIP_CHECKS=yes'
> 
jubalj@jub0:~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0294 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (4480x1600) to maximum 3D texture size (4096): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)


resulting in the above error!  'gtk-window-decorator --replace', suggested elsewhere, doesnt seem to help.

Here are the relavent portions of my xorg.conf

> Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1920 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection



Section "Monitor"
    Identifier     "CPD-G520"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 3007WFP"
    HorizSync       49.3 - 98.5
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-G520"
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:4:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GX2"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GX2"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "CPD-G520"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 2560x1600 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1920x1440 +0+0; CRT: 1600x1200 +0+0; CRT: 1280x1024 +0+0; CRT: 1280x960 +0+0; CRT: 1152x864 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0; CRT: 640x480 +0+0"
EndSection

Any help appreciated.

Thanks
Jubal

---

### Post by felixgonschorek on 2007-10-12
hi all,

i am having the same problem, nearly the same configuration (nvidia, xinerama, gutsy beta), fresh install.

if someone has a solution, i would highly appreciate if he is answering :)

---

### Post by jubalj on 2007-10-12
I got it working by dropping my resolution seems like 1920x1440,2580x1800 was a bit too much, I had to drop the first monitor to below 1600x and then twinview worked. So I've got  compiz with twinview instead of xinerama without any problems.

---

### Post by felixgonschorek on 2007-10-13
okay, i've got it working, too.
looks like xinerama is currently not supported. i used the nvidia-settings app to switch to twinview. but the gnome "erscheinungsbild" (to manage fonts, themes and effects) settings did not work. so i installed compizconfig-settings-manager and it works now.

related bug: [https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/140819](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/140819)

---


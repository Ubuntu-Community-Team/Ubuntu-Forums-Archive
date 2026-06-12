---
title: "User Switch"
date: 2006-05-30
forum: Desktop Environments
---

### Post by hanzomon4 on 2006-05-30
Okay I have a computer that is used by me and two other people, When I try to switch user I am asked to choose which Xserver. When I choose xgl I get an error message > Cannot start new display
the xserver failed perhaps it is not configured well
I have a pci nVidia GeForce FX 5500
Here is my xorg.conf > Section "Files"
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
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "NVIDIA GeForce FX 5500"
        Driver          "nvidia"
        BusID           "PCI:1:2:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
        Identifier      "DELL E153FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce FX 5500"
        Monitor         "DELL E153FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
And my gdm.conf-custom
> [daemon]

[security]

[xdmcp]

[gui]

[greeter]
Welcome=
GraphicalTheme=loginproject

[chooser]

[debug]

[servers]
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
Thanks for the help and if you need more info let me know

---

### Post by henriquemaia on 2006-05-31
This is not the answer to your problem, but I just want to remind that xgl is not stable yet. There are lots of things that don't work as expected with it.

---

### Post by hanzomon4 on 2006-05-31
Yes I understand.

---

### Post by graigsmith on 2006-06-01
many videocards can only have one 3d output at once.  so when you have one xgl session, and you try to start another, you probably can't cause the 3d hardware is already in use.

---

### Post by hanzomon4 on 2006-06-01
[QUOTE=graigsmith]many videocards can only have one 3d output at once.  so when you have one xgl session, and you try to start another, you probably can't cause the 3d hardware is already in use.[/QUOTE]

Thank you, Now I can stop and just let it go ;)

---

### Post by patrickfromspain on 2006-06-01
A question: why do you have 1=Xgl??? All the nvidida howtos I've read have 0=Xgl...

And another thing, I don't know if it's even possible to have 2 Xgl's servers running at time.

---

### Post by hanzomon4 on 2006-06-03
[QUOTE=patrickfromspain]A question: why do you have 1=Xgl??? All the nvidida howtos I've read have 0=Xgl...

And another thing, I don't know if it's even possible to have 2 Xgl's servers running at time.[/QUOTE]

It allowed me to run to xsessions one on F7 and another on F8, one had xgl the other 
the regular xserver

But I have changed it back to 0=XGL

---


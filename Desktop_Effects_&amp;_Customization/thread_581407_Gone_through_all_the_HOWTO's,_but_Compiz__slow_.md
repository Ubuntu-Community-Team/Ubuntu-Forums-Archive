---
title: "Gone through all the HOWTO's, but Compiz _slow_"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by dotancohen on 2007-10-19
I have a Dell Inspiron 6400 / E1505 with the ATI X1400 video card and 1680x1050 resolution widescreen LCD. With the ATI driver I was able to run Beryl at the native resolution with Kubuntu 7.04 (KDE desktop). Now that I have upgraded to Gutsy, Compiz is very slow and has no graphical effects. Even before I run compiz, the desktop is very slugish, ever since I installed xserver-xgl.

Here is my xorg.conf:
```

# Xorg configuration created by system-config-display

Section "ServerLayout"
        Identifier     "single head configuration"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Synaptics" "CorePointer"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Synaptics"
        Driver      "synaptics"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
        Option      "Emulate3Buttons" "yes"
        Option      "SHMConfig" "on"
EndSection

Section "Monitor"

 ### Comment all HorizSync and VertSync values to use DDC:
 ### Comment all HorizSync and VertSync values to use DDC:
        Identifier   "Monitor0"
        ModelName    "LCD Panel 1680x1050"
 ### Comment all HorizSync and VertSync values to use DDC:
        HorizSync    31.5 - 90.0
        VertRefresh  59.9 - 60.1
        Option      "dpms"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "fglrx"
EndSection

Section "Module"
       load "GLcore"
       load "glx"
       load "dri"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
       Option "Composite" "Disable"  # this makes DRI work with fglrx
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
                Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1680x1050"
        EndSubSection
EndSection

```

This is the same xorg.conf as I had in Kubuntu 7.04. I'm glad that I saved it as without it I could not enable the native 1680x1050 resolution.

This is the output of compiz in Konsole:
gutsy@gutsy-laptop:~$ compiz
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Starting kde-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

I see that it's looking for nVidia specific configuration. I have an ATI X1400. What must I configure?

Thanks in advance.

---

### Post by dotancohen on 2007-10-19
Update: fglrxinfo crashes X.

I've gotten a bit further with XGL and now this is the output of compiz:
```

gutsy@gutsy-laptop:~$ compiz
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Starting emerald
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

Also, I can move windows with ALT-left drag so I know that compiz is running. But it is unbelievably sluggish.

---


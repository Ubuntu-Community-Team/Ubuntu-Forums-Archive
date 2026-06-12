---
title: "Dual Monitor Problem"
date: 2010-05-09
forum: Desktop Environments
---

### Post by Zeenomorph on 2010-05-09
I've checked many forum posts about running dual monitors, and am still coming up empty.

I have a viewsonic 1680x1050 monitor, and was given a Philips 170s (1280x1024).  I have a Nvidia graphics card with dual monitor support.  I am running the latest Nvidia driver.  I can use the 

   sudo nvidia-settings

command, and it does seem to write to my 

     sudo gedit /etc/X11/xorg.conf

This issue that I run into everytime is the same.  I want to enable TwinView, and when I select the settings the other monitor pops to life for a second (shows a screen with the "would you like to keep these settings?") and then goes blank.  The timer on the window ends, and my settings go back to the old way.  The second monitor is only on for less than a couple seconds.

Any advice would be appreciated.

---

### Post by sir_nasty on 2010-05-09
Sounds like it could be a refresh issue.  Also, after you run "sudo nvidia-settings" from the terminal.  When you click on write to xorg.conf it should give you and option of where to save it.  if not run "locate xorg.conf" and see if you can find where it's being saved too.  However, the first thing I would do is simply go to system, administration and just load the nvidia-settings from the menu.  Hope this helps!  If not then I'd be happy to supply you with a copy of my xorg.conf file on Monday.

---

### Post by Zeenomorph on 2010-05-09
I have logged out and in to see any changes.  Nothing there.  The save to xorg.conf seems to work.  When I access the file I can see the settings.  for example TwinView "true" is there, where previously there was only a blank line.  So it seems to be able to overwrite the xorg.conf file.  In fact... before posting here, I went in and undid all the modifications that the nvidia-settings did so that I could work as normal.

Now my second monitor is just staring blankly at me.  =+(

---

### Post by sir_nasty on 2010-05-12
Here's my current Xorg.conf setup for my nvidia 7600 gt card.... does this help any?  One other thing to try is swap the monitors to the opposite ports on the video card and see if the black monitor is still black...

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer H213H"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer H213H"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    Option  	   "Below"   "Monitor0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1680x1050 +0+0, CRT-1: 1680x1050 +1680+0"
    Subsection      "Display"
            Depth   24
     EndSubSection
EndSection


Section "ServerFlags"
        # Even if mouse detection fails, X will start
        Option "AllowMouseOpenFail" "yes"

        # VT switching is disabled
        Option "DontVTSwitch" "yes"

        # X restart (Ctrl+Alt+Backspace) is disabled
        Option "DontZap" "yes"
EndSection



```

---


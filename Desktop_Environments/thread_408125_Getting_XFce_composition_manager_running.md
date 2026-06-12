---
title: "Getting XFce composition manager running"
date: 2007-04-12
forum: Desktop Environments
---

### Post by FooSoft on 2007-04-12
I'm running Xubuntu 6.10 and I'm trying to get the composition manager included w/ XFce to work, however it's not cooperating. I followed instructions several guides, but no luck. Here's my xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Buttons" "7"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 2 3 6 7"
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
    ModelName      "DELL P1130"
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       15.0 - 46.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:5:0:0"
    Option         "NoLogo"
    Screen          0
    Option         "RenderAccel"           "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:5:0:0"
    Option         "NoLogo"
    Screen          1
    Option         "RenderAccel"           "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1600x1200_85 +0+0; CRT: 1600x1200 +0+0; CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1280x720_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I'm running on an fresh install with NVidia drivers installed by the Envy scripts ([http://www.albertomilone.com/nvidia_scripts1.html)](http://www.albertomilone.com/nvidia_scripts1.html)). I'm kind of at a loss as to what I'm missing - any ideas?

---

### Post by codejunkie on 2007-04-12
> **FooSoft said:**
> I'm running Xubuntu 6.10 and I'm trying to get the composition manager included w/ XFce to work, however it's not cooperating. I followed instructions several guides, but no luck. Here's my xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Buttons" "7"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 2 3 6 7"
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
    ModelName      "DELL P1130"
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       15.0 - 46.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:5:0:0"
    Option         "NoLogo"
    Screen          0
    Option         "RenderAccel"           "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:5:0:0"
    Option         "NoLogo"
    Screen          1
    Option         "RenderAccel"           "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1600x1200_85 +0+0; CRT: 1600x1200 +0+0; CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1280x720_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I'm running on an fresh install with NVidia drivers installed by the Envy scripts ([http://www.albertomilone.com/nvidia_scripts1.html)](http://www.albertomilone.com/nvidia_scripts1.html)). I'm kind of at a loss as to what I'm missing - any ideas?

don't know if this will work for you or not, but i couldn't get it to work until i commented out the
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```
part in the /etc /X11/xorg.con file after i commented that out and restarted the xserver it was working hope this helps.

---

### Post by FooSoft on 2007-04-13
I've (inadvertently) tried that when I forgot to include it a couple of times hehe. No workie though.

---

### Post by FooSoft on 2007-04-13
Could someone who has this working maybe post a copy of their x.org (preferably nvidia but ati should be helpful as well)?

---

### Post by themtx on 2007-04-13
Hope this isn't too obvious - did you enable compositor in xfce settings manager?  check the Window Manager Tweaks icon, then Compositor tab (last on the right) - check the box for "Enable display compositing".  Woohoo, transparency.  Been using it for a while, since Beryl won't do mergedfb desktops greater than 2048 wide...

---

### Post by FooSoft on 2007-04-13
> **themtx said:**
> Hope this isn't too obvious - did you enable compositor in xfce settings manager?  check the Window Manager Tweaks icon, then Compositor tab (last on the right) - check the box for "Enable display compositing".  Woohoo, transparency.  Been using it for a while, since Beryl won't do mergedfb desktops greater than 2048 wide...

I did not do this, however I don't see this tab. Am I missing something?
[IMG]http://img53.imageshack.us/img53/5672/tweakspq4.jpg[/IMG]

---

### Post by kerry_s on 2007-04-13
If your using ubuntu xfce4 it's not built with composite support so it will never work.
You need to update your install-> [http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy](http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy)
After you update it will work.

---

### Post by FooSoft on 2007-04-13
Awesome that works! Thanks :)

---


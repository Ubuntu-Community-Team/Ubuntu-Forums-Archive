---
title: "Window decorations with Beryl missing"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by Onay on 2007-07-23
I searched all last night around the forums for a solution to fix my problem of the missing window decorations. Below is a list of all the things I have tried.

1. Enable window decorations in Beryl Mananger
2. Add "AddARGBGLXVisuals"   "True" under "device"
3. Set the "DefaultDepth" to 24 under "screen"
4. Checked to see if emerald is installed, then do emerald --replace. The terminal just hangs when that is typed.
5. Window decorations work with Metacity, but I do not have any window effects with that method.
6. Enabled nVidia drivers (a while ago).

My best guess is that emerald is not working in sync with beryl, but I could be totally wrong. I have the latest version of both beryl and emerald as well, seeing as I just installed them last night.

Here's my xorg.conf...
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	   "AddARGBGLXVisuals"   "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Please tell me if I made an error with my methods or if this could be something else.

---

### Post by Onay on 2007-07-23
Bump... anyone have any idea? I'm sort of a newbie when it comes to Linux and I'm not very familiar with many commands. :(

---

### Post by Onay on 2007-07-23
Nothing's working...

---

### Post by mrbandersnatch on 2007-07-23
Which Nvidia drivers are you using? From what I understand (and I may be wrong) theres a bug in the latest which causes decorators to be missing (I have this problem myself btw). Depending on your video card you may be able to use an older set of drivers......

---

### Post by Onay on 2007-07-23
I'm not exactly sure on how to check that, but as far as I know the drivers I have are the latest. I got them about a week ago.

How can I install older versions of the drivers? I believe that my graphics card is nvidia-legacy, so I don't know if there are newer versions of older graphics cards. Mine is the GeForce4 MX 440.

Version of my driver: 1.0-9631

---

### Post by Onay on 2007-07-23
Bump.

---

### Post by michael37 on 2007-07-23
Have you tried simply restarting compiz?  Run "compiz --replace" in the terminal (yes, terminal without a window decoration)

---


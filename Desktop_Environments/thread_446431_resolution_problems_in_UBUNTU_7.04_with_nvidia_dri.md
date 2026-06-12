---
title: "resolution problems in UBUNTU 7.04 with nvidia drivers"
date: 2007-05-16
forum: Desktop Environments
---

### Post by shivantha17 on 2007-05-16
i use ubuntu 7.04 version and i have already installed nvidia drivers for my vga card.
problem is, when i installed nvidia drivers resolution is not supported 1024*768.
pls help me,
how to add 1024*768 to my resolution list..thanx.............

---

### Post by Nythain on 2007-05-16
in terminal you could type
sudo dpkg-reconfigure -phigh xserver-xorg
or you could type
gksudo gedit /etc/X11/xorg.conf
find the section that looks like this
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```
and manually add the resolutions you want available

---

### Post by nicepants on 2007-05-16
by the way, the gui config for nvidia drivers is: ```
sudo nvidia-settings
```
actually, it's just nvidia-settings, but if you don't use sudo it won't have permissions to save your xorg.conf and you'll need to move it over to /etc/X11/ manually.

---

### Post by shivantha17 on 2007-05-18
but it doesnt work .pls help me.

---

### Post by shivantha17 on 2007-05-18
> **shivantha17 said:**
> but it doesnt work .pls help me.

can u pls upload the Geforce 6100 nvidia driver(deb file or files with dependencies) to UBUNTU 7.04.even after i can solve this.isnt it.i think i install the wrong driver.
but before welcome screen nvidia logo with full screen appeared...pls help me in any way..............

---

### Post by dfreer on 2007-05-18
what *doesn't* work? did you edit your /etc/X11/sources.list or run sudo nvidia-settings? those drivers should be in the repositories already, and if you have correctly installed your video card drivers you shouldn't need them. could you post your /etc/X11/sources.list file?

---


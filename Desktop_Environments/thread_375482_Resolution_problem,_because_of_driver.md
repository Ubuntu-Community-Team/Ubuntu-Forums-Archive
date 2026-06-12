---
title: "Resolution problem, because of driver?"
date: 2007-03-03
forum: Desktop Environments
---

### Post by masivemunkey on 2007-03-03
Hi, I'm a ubuntu and linux in general noob, I recently installed it and then used this tutorial [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)
to install beryl and the nvidia driver.  The problem is that I can't go above 1024x768, which makes me think this driver doesn't work with my card?  I have an intel M cpu with a Geforce Go 7800 GTX.  

In my xorg.conf it says:

> Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
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

Thanks for your help.

---

### Post by chewearn on 2007-03-04
To confirm that you have 3D rendering (i.e. nVidia driver is running):
```
glxinfo | grep rendering
```If it returns "direct rendering: Yes", then you are good to go.


To enable higher resolution, enter the your resolution into the xorg.conf.

Example, to use 1280x1024 with 24-bit color, the lines:
```
     SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
```Should become:
```
     SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```
After you have saved the changes, restart GDM by CTRL+ALT+Backspace, or:
```
sudo /etc/init.d/gdm restart
```

---


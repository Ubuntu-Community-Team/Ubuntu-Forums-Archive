---
title: "Quake3 problem - No fullscreen, only windowed mode"
date: 2006-09-03
forum: Gaming &amp; Leisure
---

### Post by mayamaniac on 2006-09-03
I followed this [direction]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games") to install Quake III Arena and for the most part it works. Punkbuster and Sound works also. But one problem is I can't get it to load fullscreen. In Quake3, the setting for Fullscreen is ON. I'm running 1280x1024 resolution. I have the latest nvidia driver installed with automatix and color despth is set at 24bit in xorg.conf

> Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
    Option "NoLogo" # This option disable the startup logo. optional.
    Option "RenderAccel" "true"
    Option "Triplebuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350"
    EndSubSection
EndSection

Also the game is really dark and brightness control is disabled in Quake3. Is there a fix for this also? 

Thanks for any suggestions.

---

### Post by Anduu on 2006-09-03
Are you running XGL?

For me Quake3 starts fullscreen in regular Gnome but in XGL it will only window...

---

### Post by mayamaniac on 2006-09-09
I have XGL installed but it is not running. Does XGL have to be removed or uninstalled in order for Quake3 to run fullscreen?

---

### Post by lars.vaerland on 2007-06-23
I am experiencing the same on a HP laptop running Intel 945 integrated graphics. its not only this game but 10 or 12 different games. dark colors, and windowed mode.... i do have xgl installed but not activated..

---


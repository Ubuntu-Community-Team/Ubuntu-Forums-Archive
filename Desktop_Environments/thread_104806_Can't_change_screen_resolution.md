---
title: "Can't change screen resolution"
date: 2005-12-16
forum: Desktop Environments
---

### Post by davidswe on 2005-12-16
I started my computer and discovered that my screen resolution (normally 1024x768) had changed to 640x480. When I tried to change it back, 640x480 is the only choice I'm offered. I have been Ubuntu 5.10 for some time and this is a new one on me. Has anyone got any advice?

Thanks in advance!

---

### Post by cdhotfire on 2005-12-16
Hello, it is very simple, first open up terminal and type in

```

$ sudo gedit /etc/X11/xorg.conf

```
look for this
```

Sections "Screen"
........

```
This is mine
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```
I have it set to change from 1280x1024 to 640x480.

Hop that helps.

---

### Post by aysiu on 2005-12-17
This should help:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---


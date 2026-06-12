---
title: "need 1024x860 screen res newb talk please"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by kokopelli9999 on 2007-10-23
i recently upgraded to the latest version of ubuntu on my dell inspiron e1505 and it screwed up my screen resolution.

i fixed it once before, when i first switched from windows to ubuntu but i suppose upgrading undid the fix:confused:

i have tryed:

doing the xserver thing, it doesn't give me 1024x860 as an option where ppls tell me it should

and

sudo apt-get install xserver-xorg-video-intel
this said that i have the latest version of the driver.

i have no idea what i am doing.  i am not computer oriented except that i know i hate windows.  explain this to me like you would to a six year-old.

---

### Post by ridgeland on 2007-10-26
First make a backup before editing a configuration file.
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old1
Then edit the file
$ sudo gedit /etc/X11/xorg.conf
look for 
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7300 LE"
    Monitor        "FPD1810"
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
I don't see 1024x860 as an option on my PC.  But the top shows
DefaultDepth 24
under section Depth 24 it lists 4 modes, the first is the default.  I could move 1024x768 to the front to make it the default.
That's my PC.  What do you find for your PC?

---


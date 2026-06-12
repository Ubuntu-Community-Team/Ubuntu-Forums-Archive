---
title: "Put gdm login on secondary screen"
date: 2007-08-22
forum: Desktop Environments
---

### Post by TB2 on 2007-08-22
Hi,

I've got two screens and I'd like the gdm login to show up on the second screen - the right one - instead of the left primary one. How can I do that? "SetPosition=true" and "Position=xy" values obviously don't work with the standart greeter Ubuntu offers, and only work with the "login window". I'd definetly like to have both the logo and the login line on the secondary screen. I don't care about the buttons on the bottom tho.

Any idea?

Thx!

---

### Post by mojoman on 2007-08-23
Can't you just make the right screen your primary screen? I use TwinView and with that it's possibly to configure your screens and state where the secondary screen will be placed (e.g. LeftOf, TopOf etc) and I *think* that the login always appear on the primary monitor, regardless of its position to the secondary monitor.

Give some more information, for example, what are you using for your two screens (i.e. Twinview,  Xinerama etc)? Also, posting the contents of your xorg.conf (located in /etc/X11/xorg.conf) will increase the possibility of someone being able to help.

best regards

---

### Post by TB2 on 2007-08-23
Thanks for your answer.

> **mojoman said:**
> Can't you just make the right screen your primary screen?I can't or I don't know how. I also use TwinView, but I can only configure how the screens shall be arranged, and it always takes the left one as primary. There's no option, which screen should be primary, or is it?

The relevant parts of my xorg.conf are these, and they were mostly configured by nvidia-settings. I only edited it myself in the beginning to get a resolution of 1280x1024. Now I'm using 2x 1600x1200.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

...

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

...

Section "Monitor"
    Identifier     "Generic Monitor"        # BTW this is a Sony GDM-500PS, the one I want as primary.
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony GDM-3001PT"       # This one was autodetected correctly, I didn't fill in this name.
    HorizSync       30.0 - 95.0
    VertRefresh     48.0 - 160.0
EndSection

Section "Device"
    Identifier     "8800GTS"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "8800GTS"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1600x1200 +0+0, CRT-1: 1600x1200 +1600+0; CRT-0: nvidia-auto-select +0+0, CRT-1: 1024x768 +1600+0; CRT-0: nvidia-auto-select +0+0, CRT-1: 800x600 +1600+0"
EndSection
```

---

### Post by mojoman on 2007-08-23
Hmm, I had a look at the TwinView manual [(here)]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html")  and you're probably right, at least I couldn't find any option that would do the trick. And you had already tried the orientation option, right? I'm sorry to say that I'm at my wits end, at least for now. 

Anyone else who has any bright ideas on this?

---

### Post by TB2 on 2007-08-23
I thought about starting 2 X-servers, one per screen, which would apparently also solve my other problem, that I'm dissatified with the behaviour of compiz-cube and rotate. But I don't want to mess everything up...
If I did so, would it still be possible to drag windows from one X to the other, at least with a hot key or some thing like that?

---

### Post by mojoman on 2007-10-04
> **TB2 said:**
> I thought about starting 2 X-servers, one per screen, which would apparently also solve my other problem, that I'm dissatified with the behaviour of compiz-cube and rotate. But I don't want to mess everything up...
If I did so, would it still be possible to drag windows from one X to the other, at least with a hot key or some thing like that?

I stumbled on an alternative solution to this problem when I installed Debian Lenny. You could ditch GDM and use slim as a login manager instead. It has some weaknesses (most of all that I haven't figured out how to change login session though it apparently is doable but if you're only using one desktop environment or window manager that's not an issue) but it's very easy to configure where you want the login box.

---


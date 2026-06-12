---
title: "4:3 and 16:10 resolutions"
date: 2006-02-11
forum: Desktop Environments
---

### Post by DrQuincy on 2006-02-11
I  run Kubuntu on a 4:3 monitor at 1600 x 1200.  I have just bought a new Philips monitor that can display 1680 x 1020 (16:10).  Can I easily add this new resolution to the xserver and switch between the two ratios (or even better make it automatic)?  When I plugged this monitor and and botted up it stretched 1280 x 1024 over the whole screen and the native resolution was not among the display settings?

Thanks.

---

### Post by MetalMusicAddict on 2006-02-11
Heres the relevant lines from my xorg. I have a Dell 2405 running @1920x1200. I still have to edit my config to add more widescreen resolutions but 1920x1200 is its native res so I usually run at that.

You might want to run **sudo dkpg-reconfigure xserver-xorg** in a terminal if you know what your doing.

```
Section "Monitor"
    Identifier     "DELL 2405FPW"
    Option         "DPMS"
    #HorizSync      30-101
    #VertRefresh    56-160
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "DELL 2405FPW"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by stoeptegel on 2006-02-19
It's propably 1680 x 10**5**0, just like my benq FP202W 20 inch.

You can switch the resolutions, but AFIAK you have to replace the /etc/X11/xorg.conf file and restart X with ctrl-alt-bksp to get it done.  But i'am not very good in linux yet, so this might be bull though. Also be sure to replace your monitor before you restart X, because i dunno the exact outcome when you don't. (propably just X that won't start though)

---

### Post by moreweb on 2006-06-29
Hi!
**stoeptegel** have you the Benq lcd monitor yet?
I've some problem with my configuration (Nvidia Quadro2 Pro + Benq FP202W).
Can you post your xorg monitor section? 

Do you use DVI or D-SUB connection?

Thanks!! :D

---


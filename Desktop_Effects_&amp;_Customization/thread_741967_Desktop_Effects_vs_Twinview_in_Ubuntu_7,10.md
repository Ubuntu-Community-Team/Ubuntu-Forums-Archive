---
title: "Desktop Effects vs Twinview in Ubuntu 7,10"
date: 2008-04-01
forum: Desktop Effects &amp; Customization
---

### Post by khendar on 2008-04-01
I've been fiddling with Compiz and having a degree of success. The issue is now I want to get my second monitor up and running, and it seems its not going to let me have both Advanced Desktop Effects and Twinview/Dual Display at the same time.

I'm running Ubuntu 7.10 AMD64
Nvidia 7900GT
Benq FP222W @ 1680x1050
Benq FP71G+S @ 1280x1024

If I install xserver-xgl, I can get Advanced Desktop Effects to work, but instead of getting Twinview or proper dual display I get my desktop spanned across both monitors, which doesn't work well because they're different sizes. It sets the resolution to 2960x1050 and spans the kmenu and taskbar across both monitors.

I tried running nvidia-settings to set up Twinview but I'm told that I'm not using the NVidia driver and to run nvidia-xconfig and restart xserver. This doesn't work and I discovered its because I had Xgl running.

I disabled xgl and ran nvidia-xconfig then nvidia-settings and I was able to set up Twinview, but now I cannot enable Desktop Effects.

So Is there any way to have Twinview running, but still get to use Desktop Effects ?

Cheers

---

### Post by dboot on 2008-04-02
Yes, it's very possible. I have compiz enabled with two monitors using twinview. First make sure you have nvidia drivers set up properly. Then you can use the nvidia settings manager to configure your second monitor by editing /etc/X11/xorg.conf. After you have both monitors working, with the taskbar only on one monitor for instance, you can install compiz manager and enjoy your setup. :)

I can provide a working xorg.conf if you have trouble with nvidia settings manager.

Good luck!

---

### Post by bemymonkey on 2008-04-03
Have you gotten a setup like this running for multiple monitors with separate resolutions AND separate refresh rates? I'm trying to get a CRT running with a TFT, and I'm getting 60hz on both...

---

### Post by dboot on 2008-04-04
No, I have two 19" LCD's running at the same refresh rate and resolution. However, both of those should be configurable if you know what you monitor supports.

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 8800 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 8800 GT]"
    Monitor        "Generic Monitor"
    Option         "TwinView" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "metamodes" "1280x1024,1280x1024; 1280x1024,NULL"
    Option         "NoLogo"
    SubSection     "Display"
        Modes      "2560x1024" "1280x1024,NULL"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

You can do more configuration in nvidia settings manager. Sometimes it doesn't save to your xorg.conf file so you should adjust the screens the way you want, go to save it to your xorg.conf then look at the changed file, copy the changes and then edit the file yourself.

---


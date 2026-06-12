---
title: "dual monitors - maximize window to current screen"
date: 2008-09-28
forum: Desktop Environments
---

### Post by tone33 on 2008-09-28
I am running Kubuntu with KDE 3.5.9 and have dual monitors, using nvidia twinview.  When I double click the title bar of a window it maximizes to both screens - how can i make it only maximize to the current screen?

---

### Post by ad_267 on 2008-09-28
Have you logged out and back in again or restarted? I find that happens after just activating TwinView but after a log out everything is gravy.

---

### Post by tone33 on 2008-09-28
i have.  is there a setting somewhere to "maximize to screen"?

---

### Post by tone33 on 2008-10-02
bump.

---

### Post by skullmunky on 2008-10-02
Hi,

You can fix this by editing your /etc/X11/xorg.conf file.  The options you need to set are for "TwinviewXineramaOrder".  (Xinerama is a standard XWindows extension for multiple monitors).

here's an example - you need to set the NoTwinViewXineramaInfo option to False, and you may need to set the TwinViewXineramaInfoOrder.  ( Below CRT-0 and CRT-1 are my monitors.)

```

Option         "NoTwinViewXineramaInfo" "False"
Option         "TwinViewXineramaInfoOrder" "CRT-0, CRT-1"

```

```


Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "NoTwinViewXineramaInfo" "False"

    Option         "TwinViewXineramaInfoOrder" "CRT-0, CRT-1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1024x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

see the reference for more explanation of the the nvidia options
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-d.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-d.html)

---

### Post by tone33 on 2008-10-03
Works great thanks!  Who would thought to just read the documentation! :)  Seriously, thanks.

---


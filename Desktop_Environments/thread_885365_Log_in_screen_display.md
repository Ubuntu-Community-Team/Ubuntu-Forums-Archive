---
title: "Log in screen display"
date: 2008-08-10
forum: Desktop Environments
---

### Post by jlhughes on 2008-08-10
Ever since Hardy, Ubuntu has been unable to correctly figure out my video setup. The "default" is some strange low-color, 900x600 display. It also does not correctly fill the screen, either the log in screen or the user desktop.

I reported this problem once before [here]("http://ubuntuforums.org/showthread.php?t=852458"). At that time I was able to use an old xorg.conf file to replace Hardy's xorg.conf.  This time, however, that trick didn't work.

Using gksudo displayconfig-gtk I was able to set the monitor to my Viewsonic VA721 (using the VA720 setting) and I set the video card to SiS 530.

This works perfectly on the desktop. HOWEVER, at the log in screen, all I see is the Ubuntu logo and ub.  The rest of the word and the log in form are not visible. Neither is the lower panel.

How do I adjust the screen resolution on the log in screen?

---

### Post by cdtech on 2008-08-10
You need to add a virtual display to your /etc/X11/xorg.conf file as I did here:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        **Virtual     1440 900**
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection
```
Use the size of your own in bold.......

---

### Post by jlhughes on 2008-08-10
Excellent!  Works like a charm with Virtual line and the defaults for my resolution. 

Thank You!

---

### Post by cdtech on 2008-08-10
Your welcome.....

---


---
title: "Beryl takes away title bar"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by Doughnut3 on 2008-01-02
I recently installed beryl to inpress my friends and it does, but there is no title bar.  I have everything i can think of installed.  Video card is installed and the window decoration is on.  I have read of many people who have my problem also, but none seem to help. I am a total ubuntu noob.  Only seen it once before.

---

### Post by runemaste644 on 2008-01-02
Ive had this problem too. This is my 1st screen section in my xorg.conf after i fixed the problem.
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60" "1920x1200@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60"
    EndSubSection
EndSection
```
Try adding the ```
Option "AddARGBGLXVisuals" "True"
```
between the DefaultDepth and SubSection "Display" and see if that fixes it. It worked for me.

---

### Post by Mr Greencastle on 2008-01-02
Press ALT+F2 then type in ```
gtk-window-decorator --replace
```

Mr Green

---


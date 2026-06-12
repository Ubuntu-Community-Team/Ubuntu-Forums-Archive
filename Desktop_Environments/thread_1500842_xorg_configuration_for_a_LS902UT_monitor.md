---
title: "xorg configuration for a LS902UT monitor"
date: 2010-06-03
forum: Desktop Environments
---

### Post by mdeadlock on 2010-06-03
Hello,

I'm new to ubuntu (10.04 LTS) and was wondering how to configure xorg in order to get a decent display with Iiyama LS902UT monitor as a 800x600 is not really funny.
I tried to google but first step i tried from [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config) told me to try a  sudo Xorg -configure
that unfortunately ended with:
```

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
```So my simple question is :
 - how do i create this xorg.conf file
 - what is should put in it in order to let gnome/xorg better recognize my 19" monitor (currently said as 'unknown')

Should i have posted in wrong forum, do not hesitate to move and tell me.

Thanks.

---

### Post by mdeadlock on 2010-06-04
I finally succeeded by appling my old xorg.conf configuration by creating /etc/xorg.conf and setting it to
```
Section "Monitor"
        Identifier      "Monitor0"
        VendorName      "IIyama"
        ModelName       "LS902UT"
        DisplaySize     360 270
        #DisplaySize    548 406
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier "Screen"
        Device     "Card"
        Monitor    "Monitor0"

    Subsection "Display"
        Depth       24
        Modes       "1600x1200" "1280x1024" "800x600" "640x400" "1400x1050"
    EndSubsection
EndSection

```

Resolution was fine with gdm but i had to change it to 1600x1200 once gnome was started.

Hope this could help.

---


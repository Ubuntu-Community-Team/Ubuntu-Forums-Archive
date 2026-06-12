---
title: "Video resolution limited after update"
date: 2009-05-03
forum: Desktop Environments
---

### Post by lnxbrittan on 2009-05-03
I installed 9.04 in a desktop AMD Athlon with an ATI RADEON 7500 graphics controller and an attached ViewSonic 19” LCD monitor several weeks ago. This monitor looks best with the resolution set to 1680 x 1050 @ 60Hz and at install that's what Ubuntu set it to. Then after some number of updates suddenly the resolution has been reduced to a maximum of 1280 x 1040. How can I fix this?

Thanks,
Mike

---

### Post by PacSci on 2009-05-03
I have problems with a ViewSonic 19" monitor too. But can you specify which updates you installed?

(By the way, you're double posted.)

---

### Post by ajgreeny on 2009-05-03
You could try booting to recovery mode and using the xfix that appears in the menu, however, have you looked in System > Preferences > Display to see if you can change it back?  I will assume you have.  If you were using a proprietary driver you may need to reinstall it, if you are using the open source driver it may require you to manually edit the /etc/X11/xorg.conf file by adding the resolution you want and your screen refresh rates, in the format shown below.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80 # edit this to your figures.
            VertRefresh    50-75 # edit this to your figures.
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1680x1050" # add other resolutions you may need
    EndSubSection
EndSection
```

---


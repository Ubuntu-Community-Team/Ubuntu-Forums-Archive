---
title: "KDE dpi with nvidia 3d drivers"
date: 2006-02-23
forum: Desktop Environments
---

### Post by kkallio on 2006-02-23
After struggling with obnoxiously large fonts in kubuntu I finally managed to get it right. So for those who have the same problem, the correct procedure is to change the proprietary nvidia driver settings. (I've installed the latest nvidia 3d drivers from nvidia site, following method 2 described here: [http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074"))

The other solutions for the dpi problem proposed on the web are:

1) change the dpi setting in /etc/kde3/kdm/kdmrc
ServerArgsLocal=-nolisten tcp -dpi 75
Won't do it.

2) edit the DisplaySize parameter in xorg.conf as instructed in this thread
[http://kubuntuforums.net/forums/index.php?topic=1012.msg5679#msg5679]("http://kubuntuforums.net/forums/index.php?topic=1012.msg5679#msg5679")
Won't do it.

Rather, you should add the "DPI" option to the "device" Section in xorg.conf:

```
sudo nano /etc/X11/xorg.conf
Password:

Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
    Driver         "nvidia"
    Option         "DPI" "96 x 96"
EndSection
```

Hope this helps those who have the same problem... Solutions 1) and 2) might solve it for other drivers, but it seems that nvidia drivers override this value.

Thanks for the tip go to [http://dingoskidneys.com]("http://dingoskidneys.com/cgi-bin/pyblosxom.cgi/nvidiadpi.html?showcomments=yes").

---

### Post by tlindner on 2006-02-23
This was working fine for me right up until I dist-upgraded in dapper today.  Back to big big fat fonts... anyone else have this problem?

---


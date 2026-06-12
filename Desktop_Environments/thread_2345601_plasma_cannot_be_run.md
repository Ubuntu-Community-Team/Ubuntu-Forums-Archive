---
title: "plasma cannot be run"
date: 2016-12-06
forum: Desktop Environments
---

### Post by Shura0 on 2016-12-06
Hi,  Everything worked well, but once it broke with no reason. Now plasmashell cannot be run, when I try to start it in terminal, it prints out:      
```
kscreen: Primary output changed from KScreen::Output(Id: 575 , Name: "DVI-I-3" ) ( "DVI-I-3" ) to KScreen::Output(Id: 575 , Name: "DVI-I-3" ) ( "DVI-I-3" )
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
org.kde.plasma: unversioned plugin detected, may result in instability
No metadata file in the package, expected it at: "/home/shura/&#1048;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103;//metadata.desktop"
No metadata file in the package, expected it at: "/home/shura/&#1048;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103;//metadata.desktop"
No metadata file in the package, expected it at: "/home/shura/&#1048;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103;//metadata.desktop"
kscreen: Primary output changed from KScreen::Output(Id: 575 , Name: "DVI-I-3" ) ( "DVI-I-3" ) to KScreen::Output(Id: 575 , Name: "DVI-I-3" ) ( "DVI-I-3" )
Failed to create OpenGL context for format QSurfaceFormat(version 2.0, options QFlags(), depthBufferSize 24, redBufferSize -1, greenBufferSize -1, blueBufferSize -1, alphaBufferSize 8, stencilBufferSize 8, samples -1, swapBehavior 2, swapInterval 1, profile  0) 
Application::crashHandler() called with signal 6; recent crashes: 1
/usr/bin/plasmashell  --crashes 1 &
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = plasmashell path = /usr/bin pid = 6627
KCrash: Arguments: /usr/bin/plasmashell 
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi from kdeinit
sock_file=/run/user/1001/kdeinit5__0

(process:6638): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(plasmashell:6627): GLib-GIO-ERROR **: inotify read(): Bad file descriptor
[1]    6627 trace trap (core dumped)  plasmashell
```

Driver is Nvidia, video card is GeForce 710.  If I try to run plasma under 'root' user it works well. Also I have tried to create new user and run plasma with no success. Seems like it's permissions issue, but I do not know what I should look. Please help.  P.S. If I remove nvidia driver and install vouveau then plasmashell works, but sometimes it freezes my PC so deep I have to use reset, so I would like to use nvidia drivers.

---

### Post by Kirboosy on 2016-12-06
Hi Shura0,

That sounds like a permission issue. I have heard success with creating a new user and see if that fixes the issue. After that you can migrate the files from the old account over to the new. Or you can try to take on the arduous task of figuring out what permissions are wrong. 

Hope that helps!
~Caboose

---

### Post by Shura0 on 2016-12-07
Hi Caboose885

I have tried this. It does not work anyway.

---

### Post by Kirboosy on 2016-12-08
Hey Shura0, 

Sorry I misread your post the first time through. Didn't see the fact that you had tried to create a new user. My apologies! 

How have you installed the Nvidia driver? Are you using the driver manager built into Ubuntu or did you download the drivers directly from Nvidia?

~Caboose

---

### Post by Shura0 on 2016-12-09
It's installed with *apt-get install* from standard repository

---

### Post by Kirboosy on 2016-12-09
What Nvidia version number did you install? Also what version of Ubuntu are you running this on? Ubuntu 16.04 32 bit?

---

### Post by Shura0 on 2016-12-27
Sorry for long delay

Ubuntu 16.04.1 LTS 64bit

> $ dpkg -l | grep nvidia
ii  nvidia-304                                      304.132-0ubuntu0.16.04.2                      amd64        NVIDIA legacy binary driver - version 304.132
ii  nvidia-current                                  304.132-0ubuntu0.16.04.2                      amd64        Transitional package for nvidia-current
ii  nvidia-opencl-icd-304                           304.132-0ubuntu0.16.04.2                      amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                 361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver


---


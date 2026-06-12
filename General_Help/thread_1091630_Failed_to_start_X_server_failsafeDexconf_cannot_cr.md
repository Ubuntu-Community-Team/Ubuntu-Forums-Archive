---
title: "Failed to start X server: failsafeDexconf cannot create directory"
date: 2009-03-09
forum: General Help
---

### Post by spejz on 2009-03-09
Hello all,

Ubuntu 8.10 failed to start the X server. I've got the following output:

mkdir: cannot create directory '/tmp/dexconf-tmp-6323': Too many links
failsafeDexconf: error: creation of temporary work directory "/tmp/dexconf-tmp-6323" failed
Warning: Could not generate /etc/X11/xorg.conf.failsafe for vesa driver

I have not changed any configuration explicitly. I have got enough disk space (only 18% in use of my 40GB /dev/sda1 partition) and a fschk has checked it without any problems.

The error message is quite vague and I am out of ideas.
I hope that some of you can help me with this.

Greetings,
Christophe

---

### Post by Neo_The_User on 2009-03-09
post your /etc/X11/xorg.conf file

---

### Post by spejz on 2009-03-09
```

Section "ServerLayout"
    Identifier    "Layout"
    Screen    0   "Screen0" 0 0
EndSection

Section "Module"
    Load          "glx"
End Section

Section "ServerFlags"
    Option        "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Unknown"
    ModelName    "Seiko"
    HorizSync    49.4 - 74.1
    VertRefresh  40.0 - 60.0
EndSection

Section "Device"
    Identifier   "Configured Video Device"
    Driver       "nvidia"
    Option       "NoLogo" "True"
EndSection

Section "Device"
    Identifier   "Device0"
    Driver       "nvidia"
    VendorName   "NVIDIA Corporation"
    BoardName    "Quadro NVS 160M"
EndSection

Section "Screen"
    Identifier   "Default Screen"
    Device       "Configured Video Device"
    Monitor      "Configured Monitor"
    DefaultDepth 24
EndSection

Section "Screen"

#Removed Option "metamodes" "1920x1200 @2944x1200 +0+0"
    Identifier   "Screen0"
    Device       "Device0"
    Monitor      "Monitor0"
    DefaultDepth 24
    Option       "TwinView" "0"
    Option       "metamodes" "nvidia-auto-select +0+0"
    SubSection   "Display"
        Depth    24
    EndSubsection
EndSection

```

I know that there are maybe some strange parts in it, but these are the result of a projector I used a few weeks ago. I don't think this has something to do with my problem because I used my laptop more then 10 days without any problems (and I restart daily).

---

### Post by spejz on 2009-03-09
I have tried a little bit more. Now I am pretty sure that it has to do with mkdir.
When I log in on tty1 and I do the following:
```

$ls -l /
...
>drwxrwxrwt 12 root root 4096 2009-03-10 02:21 tmp # green color
...
$cd /tmp
$ls -al
>total 8
>drwxrwxrwt 65528 root root 4096 2009-03-10 02:20 . # green color
>drwx-r-xr-x 20 root root 4096 2009-03-10 02:06 .. # blue color
$touch file
$ls -l
>
$mkdir test
>mkdir: error: cannot create directory 'test' : Too many links

```
/tmp is mounted properly and I have done fsck without any result.

---


---
title: "Problem with visual effects"
date: 2009-07-31
forum: Desktop Environments
---

### Post by lovejames on 2009-07-31
Hi,

I am a newbie of ubuntu. I am not able to enable visual effects on my desktop. After searching for a few threads about the issue, I have done a Compiz Test. Following is the result.

```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```Can somebody help to figure out what is wrong with my system? I didn't understand what "Software Rasterizer in use" means. Any help is greatly appreciated.

---

### Post by ajgreeny on 2009-07-31
I think you could well be unlucky with compiz because your video card (sis M650/740) is not very well supported, like most sis cards, I'm afraid.  You may have to accept a non compiz desktop.

---

### Post by lovejames on 2009-07-31
The other strange thing that I have noticed was the weired display settings. I generally get 1024X768 resolution. But if I boot up the computer without switching on the monitor, it loads 960X600 resolution. I mean, I just switch on the CPU but not the monitor. I have to restart the system by keeping the monitor ON to get the original resolution. I really didn't understand why this is happening. Do I have to necessarily keep the monitor ON every time I switch on the computer??  Or is this also a funny trick played by my poor SIS card??

---

### Post by ajgreeny on 2009-07-31
This is perhaps a result of the new and better(?) xorg in jaunty.  There is not much of an xorg.conf file anymore, where all the info about resolution was stored, and the theory is that if you change your monitor it will be detected and the appropriate resolution used.  Perhaps your settings are not being rememeberd by the system, and without the monitor the system reverts to a lower res.

---

### Post by lovejames on 2009-08-01
Thanks for the replies greeny. But is there a work-around for these issues??

---

### Post by ajgreeny on 2009-08-01
You may be able to manually edit your config file ```
gksudo gedit /etc/X11/xorg.conf
```and add the resolution you want by adding the information in the following pattern
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```I have left out all the text at the top, this is just the config part.  Use your own figures, of course, which you ought to be able to find in any manual you have for the monitor, or on the net.

---

### Post by lovejames on 2009-08-01
Bingo.. it worked. Thanks a lot ajgreeny.

---

### Post by ajgreeny on 2009-08-01
Great!
Although the xorg.conf is nearly empty on a default install of ubuntu, if there is any config information in it, that is used by the system, and that way you can force ubuntu to use resolutions that are not automatically detected.  It can be very useful in situations like yours.

---

### Post by lovejames on 2009-08-02
Could you also help me with another issue I have with Ubuntu at the following thread?

[http://ubuntuforums.org/showthread.php?t=1228920](http://ubuntuforums.org/showthread.php?t=1228920)

---

### Post by ajgreeny on 2009-08-02
Sorry, I have no knowledge of wubi at all, so can't help on this problem.

---


---
title: "[Solved] Can't activate visual effects"
date: 2009-08-23
forum: Desktop Environments
---

### Post by Dreadlock man on 2009-08-23
Hi guys, new at this forum and ubuntu as well. I'm trying to activate the visual effects for the desktop,compiz, but it doesn't want to work. I can't activate the "normal" visual effects(a popup windows says that the changes can't be made on the desktop). I have an ATI radeon HD3200 graphic card. I was using the manufacturer's drivers but I found a bug switching the video to full screen on the movie player(Ubuntu crashed). Now I'm using the open source driver for ATI cards, but I'm not able to run compiz. lspci|grep VGA command gives me:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
```and glxinfo|grep vendor command:
```
unknown chip id 0x9612, can't guess.
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

```and when I try to activate compiz (compiz --replace) gives me:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```Seems like the XGL is missing...
the xorg.conf file is:
```
Section "Device"
    Identifier    "Radeon HD3200"
    Driver          "ati"
    BusID        "PCI:1:5:0"
    Option        "XAANoOffscreenPixmaps"
    Option        "TripleBuffer"
EndSection

Section "Monitor"
    Identifier    "HP Mon"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "HP Screen"
    Monitor        "HP Mon"
    Device        "Radeon HD3200"
    DefaultDepth    24
EndSection
Section "DRI"
    Mode 0666
EndSection
Section "Extensions"
    Option "Composite" "Enable"
EndSection
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "HP Screen"
EndSection
```
I've also tried putting "radeon" in the driver setting, like another thread says but nothing happened
Anyway.. is there a way to turn on this feature without using the ATI proprietary driver?

Thanks a lot

---

### Post by andrea000 on 2009-08-23
You need proprietary drivers to run compiz.How did
you install the drivers and did you install compiz
config setting manager?

---

### Post by Dreadlock man on 2009-08-23
Thanks for your answer Andrea. Yes I've installed the compiz config setting manager(ccsm) but I think that only works if you have activated the visual effects and so far I couldn't. I've followed the steps given _[here]("https://help.ubuntu.com/community/RadeonDriver")_ to configure the open source driver, but what is calling my attention is the message: 
```
Cheking for Xgl: not present 
```when I'm trying to activate compiz.
If you see the code posted in the last message you'll see that the compiz doesn't get activated because of the lack of the XGL server. I've read that XGL-server its not being supported anymore in Jaunty..is this true?

---

### Post by bapoumba on 2009-08-23
[http://ubuntuforums.org/showthread.php?t=1133844](http://ubuntuforums.org/showthread.php?t=1133844)
[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

Please see these links, you may find something that will help you.

---

### Post by Dreadlock man on 2009-08-23
This is what compiz-check gives me:
```
 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 
```

Any ideas of what's happening? What does it mean with   "Software Rasterizer in use".
Everything seems to indicate that I can't activate compiz without using the proprietary driver. So I should start to look for a proprietary driver release who doesn't have the bug that I mentioned earlier.

---

### Post by zeealpal on 2009-08-24
> **Dreadlock man said:**
> Hi guys, new at this forum and ubuntu as well. I'm trying to activate the visual effects for the desktop,compiz, but it doesn't want to work. I can't activate the "normal" visual effects(a popup windows says that the changes can't be made on the desktop). I have an ATI radeon HD3200 graphic card. I was using the manufacturer's drivers but I found a bug switching the video to full screen on the movie player(Ubuntu crashed). Now I'm using the open source driver for ATI cards, but I'm not able to run compiz. lspci|grep VGA command gives me:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
```and glxinfo|grep vendor command:
```
unknown chip id 0x9612, can't guess.
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

```and when I try to activate compiz (compiz --replace) gives me:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```Seems like the XGL is missing...
the xorg.conf file is:
```
Section "Device"
    Identifier    "Radeon HD3200"
    Driver          "ati"
    BusID        "PCI:1:5:0"
    Option        "XAANoOffscreenPixmaps"
    Option        "TripleBuffer"
EndSection

Section "Monitor"
    Identifier    "HP Mon"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "HP Screen"
    Monitor        "HP Mon"
    Device        "Radeon HD3200"
    DefaultDepth    24
EndSection
Section "DRI"
    Mode 0666
EndSection
Section "Extensions"
    Option "Composite" "Enable"
EndSection
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "HP Screen"
EndSection
```
I've also tried putting "radeon" in the driver setting, like another thread says but nothing happened
Anyway.. is there a way to turn on this feature without using the ATI proprietary driver?

Thanks a lot

I noticed that it said glx. You nneed the propietry ATI drivers, which ar flgrx. Get them from the ATI website.

---

### Post by Dreadlock man on 2009-08-24
Finally, I've downloaded the lastest ATI drivers from the AMD website. I've installed them and now compiz runs perfect. Also the video bug has dissapeared, I've played the same  video in fullscreen an works without complaints. So I think that the bug was in the drivers that comes with ubuntu by default. Thanks to all. Solved

---

### Post by bapoumba on 2009-08-24
I've edited the main thread title accordingly, and added a "solved" tag.

---


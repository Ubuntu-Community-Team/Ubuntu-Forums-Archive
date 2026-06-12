---
title: "Desktop, plasmoids missing + minor bugs after KDE 4.3 install"
date: 2009-08-09
forum: Desktop Environments
---

### Post by pumrel on 2009-08-09
Hello,
I've got some issues with my KDE desktop. In fact, there is none. Instead of background there only small squares, there is no option to add widgets (either on the panel or in the top right corner), right click on the desktop does nothing and the KDE menu sometimes opens in the top left corner.

I installed Kubuntu today and then the fglrx drivers thanks to the guide at wiki.cchtml.com and everything worked flawlessly. I think it may have been caused by the installation of KDE 4.3 which I've done afterwards. 

Could anyone please help me?  Any help would be appreciated.

[[IMG]http://img14.imageshack.us/img14/8784/desktopcxh.th.png[/IMG]]("http://img14.imageshack.us/i/desktopcxh.png/")

Xorg.conf
```
Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "VideoOverlay" "off"
    Option        "OpenGLOverlay" "off"
    Option        "TexturedVideo" "on"
    BusID       "PCI:1:0:0"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "True"
EndSection

```

---

### Post by krazyd on 2009-08-09
could be something screwy with your kde configuration. You could try backing up and then deleting .kde/ in your home dir to get back to the default KDE installation.

see here [http://ubuntuforums.org/showthread.php?p=7745410#post7745410](http://ubuntuforums.org/showthread.php?p=7745410#post7745410)

---

### Post by pumrel on 2009-08-16
Thank you for the reply and sorry for the late answer. I haven t been on PC recently.
Well, I tried deleting the folder .kde but then after restart messages pop up that it is not possible to write certain files in the .kde directory.

I just wonder, is there a possibility to install KDE 4.3 alongside the old one and then revert to the old one if necessary?

---

### Post by krazyd on 2009-08-16
What error messages are you getting after restart?

---

### Post by pumrel on 2009-08-17
Well, I can't reproduce it anymore. I tried what you have written in your other thread and it seems that I missed one important step - I didn't log out off the session - and when I did it, it did the trick. So now, everything works fine.
Thank you very much.
However, there seems to be one small problem. Everytime I start Kubuntu the compositing is disabled by default and I have to enable it by the keyboard shortcut. Sometimes, I get a message that some application blocked it. Do you have any idea what it could be due to ?

---

### Post by krazyd on 2009-08-18
Is Desktop Effects enabled in System Settings?

What is the name of the process which blocks compositing?

Kwin (the KDE window manager & compositor) automatically disables compositing if it detects that the frame-rate is too low. I think the problem probably is that the fglrx driver is a little buggy and so kwin detects a low framerate and disables compositing.

Hopefully by Karmic we will have open-source 3D for the latest ATI cards, which works without having to install fglrx.

What is your graphics card?

---

### Post by pumrel on 2009-08-18
Yeah, the effects are still enabled, it's the compositing which is dead.
I can't tell which process is the cause, because the message doesn't say. However I tried to disable my SuperKaramba desklets and it seems that it might have been it. (?)
I've got ATI Radeon 2600 HD PCI and using the latest 9.7 Catalyst Driver. It was quite tricky to install them, but as I'm not having any critical issues with suspending to disk I think I'm pretty lucky, although it takes ages to suspend and recover.
I hope you're right about the drivers. Is it the Radeonhd driver?

---

### Post by krazyd on 2009-08-18
yes - radeon or radeonhd. The current progress is encouraging, see here: [http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)

---


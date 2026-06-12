---
title: "Feisty resolution problem"
date: 2007-04-20
forum: Desktop Environments
---

### Post by Boule on 2007-04-20
So I installed Feisty on my desktop (graphic card: nvidia geforce fx 5600), I installed the nvidia drivers, enabled them and everything, and I still can't change my resolution, it's stuck at 800x600.
I even try dpkg-reconfigure xserver-xorg, that worked on edgy.

What else can I try to change my resolution ? This is driving me crazy !

Thanks for your help

---

### Post by black_magician on 2007-04-20
it seems like alot of nvidia users (me included) are having problems with resolution.  I haven't found a working solution yet.

maybe this can help though
[http://ubuntuforums.org/showthread.php?t=414020](http://ubuntuforums.org/showthread.php?t=414020)

---

### Post by Boule on 2007-04-20
I could change my resolution by disabling the nvidia drivers and going back to "nv"... But that's not good enough, I want to install beryl !

In the thread you posted, it says that "older cards" should use legacy drivers instead. What is old ? Does it include my 5600 ? To enable the desktop effects, it downloads the nvdia-glx package, not the legacy !

---

### Post by JumboJr2 on 2007-04-20
You should be supported by the lastest and greatest. See for yourself at the following.  [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")

---

### Post by Boule on 2007-04-20
So I wasn't able to solve my problem yet...
I also tries installing the nvidia drivers on a laptop (geforce4), and when I rebooted, I had a black screen with weird shapes/colors...

Is there a problem with the nvidia drivers ? isn't there a way to fix them ?

---

### Post by sarracenia88 on 2007-04-20
I am a geforce 7600 user and I didn't have a problem changing my resolution to 1280x1024. I just went into 

*sudo nano /etc/X11/xorg.conf*

You just have to change all of the following so that they have your desired resolution

[I]Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes       "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes       "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
[/I]

Then just restart you xserver. 

The large screen section can be found at the bottom of your xorg file.

Hope this helps

I also use envy for installing my nvidia drivers. it works really well

*[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)*

---

### Post by Boule on 2007-04-21
I can cahnge my resolution, but not when I'm using the nvidia driver !!

---

### Post by sarracenia88 on 2007-04-22
You may have to reinstall your drivers. I would suggest using envy in the link I gave you above, then editing your xorg file after it has been reinstalled.

---


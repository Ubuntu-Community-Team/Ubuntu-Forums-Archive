---
title: "[SOLVED] Screen resolution issues with video card. Need to reset default resolution."
date: 2008-11-11
forum: Desktop Environments
---

### Post by Chou on 2008-11-11
I'm not quite a beginner at linux, but I've encountered a problem that I've never had to deal with before.

I installed Ubuntu 8.10 and began installing my NVIDIA Quadro FX 540 card. The driver works fine, as it displays the login screen perfectly and in a super high resolution, I love it!

However, when I log in, the screen goes black and I get a signal problem message. Meaning that the resolution that it's now defaulting to is too high to display on my LCD monitor.

I'm still able to log into the Failsafe Terminal, though. So here's my question...

Where is the file that contains the information on the default resolution, refresh rate, color depth, etc, and how do I go about changing it?

I gotta get it back to 800x600 32bit 60hz

---

### Post by hictio on 2008-11-11
The configuration file is the '/etc/X11/xorg.conf' is a plain text file, that you have to edit via sudo, make a backup before editing it, just in case.
What you might try is forcing a mode onto the section "Screen" to use the 800x600 resolution, by leaving only that resolution available. This is an exampple from my desktop's config file:

```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung SyncMaster 920NW"
        Device          "NV11 [GeForce2 MX/MX 400]"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"

        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x1024" "1280x960" "1024x768" "800x600"
                Viewport        0 0
        EndSubSection
EndSection

```

---

### Post by Chou on 2008-11-13
thanks! mine was more like this

```
Section "Screen"
        Identifier      "Default"
        Monitor         "Default"
        Device          "Default"
        Defaultdepth    24

        SubSection "Display"
                Depth           24
        EndSubSection
EndSection
```


So i simply changed the monitor to the actual model number, added a "DefaultMode" line and basically tricked it into screwing up... haha!

now the login screen is at the wrong resolution, but i have it set to autologin anyway.

Thanks for the help :D

---

### Post by hictio on 2008-11-13
Are you gonna leave it at 800x600 for good?
The login screen is at what resolution? 640x480?

---


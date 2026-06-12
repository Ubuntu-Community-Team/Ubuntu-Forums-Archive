---
title: "window title bars gone with beryl, ATI MOBILITY FireGL V3200 and XGL"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by toobitz on 2007-04-30
After upgrading to feisty, the title bars of all windows are not being displayed correctly. I just see a small portion of it on the upper left and the upper right corner of the window but between everything is missing and I see what's behind the window.

I am using beryl with xgl and the following startup (/usr/bin/startxgl.sh):
```

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 6
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

```

these are the relevant parts in my xorg.conf:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "aticonfig-Screen[0]"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        #Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        #Option         "AddARGBGLXVisuals" "True"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "0"
        Option          "Composite"     "0"
EndSection

```

I've been desperately trying to fix this: restarted, deleted ~/.beryl, ~/.beryl-managerrc, ~/.emerald,~/.gconf, ~/.gconfd, messed around with xorg.conf - nothing helped. Has anyone got this setup (or similar) working? I'd be very glad for any hint. Thanks!

---

### Post by toobitz on 2007-04-30
OK, I've gotten a step further: I finally noticed that my problem is that I was using XGL, but the new ubuntu beryl packages simply do not contain beryl-xgl - why this is so is beyond me. I've tried a very ugly hack: downloaded beryl-core_0.2.0~0beryl1_i386.deb from the beryl repositories, extracted the .deb and copied the beryl-xgl contained in that package to /usr/bin. Now everything is (so far) working as before, although I have the impression the whole window management is now somewhat slower than before (under edgy).

My questions for the gurus here:

[LIST=1]
[*] why is beryl-xgl missing? Am I missing something here?
[*] Is there a problem with XGL? Should it not be used?
[/LIST]

---

### Post by teh.element on 2007-04-30
I had the same problem, and after messing with some of the stuff, xserver would not start. I gave up...I would love to have it fixed

---

### Post by Fylk on 2007-04-30
This may seem completely idiotic, but disable and then restart window decorations.

---

### Post by toobitz on 2007-04-30
Thanks Fylk, but I've already tried that - several times in fact, by itself and in combination with other measures. Didn't help at all.

But as I wrote, my problem clearly was that I was lacking beryl-xgl whereas I had my gnome-session configured as running under XGL. What I've done now is the following:

1. added the following line to /etc/apt/sources.list:

```

deb http://ubuntu.beryl-project.org feisty main

```

2. started synaptic, reload, search for 'beryl-core'
3. selected the package, clicked on "Package" in the menu and under "Force Version..." selected "0.2.0~0beryl1 (feisty)" instead of the default "0.2.1.dfsg+git20070318-0ubuntu2 (feisty)", then clicked "Force Version"
3. Apply

That did it for me - it installed the older beryl-core package (0.2.0) which holds beryl-xgl. Now even the speed is perfect.

---

### Post by dogmir on 2007-04-30
that worked awesome thanks....

---

### Post by ArukiRei on 2007-04-30
Perfect.

Thanks toobitz, that worked for now. 

You rawk! :guitar:

---

### Post by djrobthaman on 2007-04-30
Hey toobitz,

I have the same exact problem that you had before you fixed it.  I tried fixing it the way you did, but now whenever I run beryl manager the screen goes all white (except fot the mouse cursor and the update notification bubble that pops up because it wants me to upgrade the beryl manager back to the version it downgraded from).  Do you know of any method to fix that???

Thanks

PS  I'm using an ATI radeon X1300 all-in-tv wonder

---

### Post by toobitz on 2007-05-01
Hmm, I never had this problem with the white screen but I recall that I read about that quite a lot on the web while searching for a solution to my problem.. did you do that already? Here are some hints:

[http://ubuntuforums.org/showthread.php?t=362381&highlight=beryl+white+screen]("http://ubuntuforums.org/showthread.php?t=362381&highlight=beryl+white+screen")
[http://mepislovers.org/forums/archive/index.php/t-2671.html]("http://mepislovers.org/forums/archive/index.php/t-2671.html")

Also, did you check the beryl forums on [http://forum.beryl-project.org/]("http://forum.beryl-project.org/")

You may also want to check [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL"), this is where I got the hint to downgrade beryl-core.

I'm sorry I can't be more specific, but as I said, I never experienced this problem myself.

BTW: I really don't know how 'clean' my 'fix' is as I am now using a different beryl-core version as the rest of the beryl packages, but I've been working for some time with this setup now and I haven't had any problems so far. It's just that I've been using XGL before and I couldn't get beryl to work without it on feisty. I'm sure the developers have their reasons for not including beryl-xgl in the ubuntu packages - as for me, I just don't see them. Maybe there is someone here who can enlighten me about that.

---

### Post by SuperAndy on 2007-05-02
not sure if this will help, but i had the same problems. beryl would only load metacity, without the beryl window manager, and hence I had no real control over my windows. however, loading beryl with this:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl-manager

solved the problem. this was for the lack of support for non power of two textures though.

meh, might work.

---


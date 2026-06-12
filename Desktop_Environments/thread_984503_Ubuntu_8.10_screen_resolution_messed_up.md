---
title: "Ubuntu 8.10 screen resolution messed up"
date: 2008-11-16
forum: Desktop Environments
---

### Post by samrohde on 2008-11-16
I booted my computer and my screen resolution is messed up throughout the entire computer including GRUB and the entire GUI. It took off half a task bar thickness(12 pixels) all the way around. I tried going into System > Preferences > Screen Resolution and I tried every resolution but all of them where the same. I am using an Olevia 232v 32" wide screen TV/Monitor connecting the computer to the TV with a VGA cable. My computer's Video/Graphics card is an Intel Graphics Media Accelerator 950, the computer processor is an Intel Celeron Processor 420. I don't know if the CPU is a 32 or a 64 bit, but I am running the 32 bit Ubuntu version. I tried booting into recovery mode and I went to xfix but it didn't fix the problem. How can I fix this problem? I have never had this problem before, until I upgraded to Ubuntu 8.10 from 8.04.

---

### Post by ajgreeny on 2008-11-16
I had a similar problem with my graphics card/monitor setup which I solved by adding the screen information from a previous (dapper?) xorg.conf file to that of 8.10 so it looks like this, with the resolution info included.:-

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Previously I had a problem with the guest login as it would not remember the resolution I set, and I had to reset it each time I logged in as guest.  That would be useless for a casual user, of course.  Also the login screen was much too large and cut of the options at the bottom, so I could not do anything except login.  The xorg.conf changes made all the difference, and now all is well.  I thought xorg.conf was now almost un-needed, but it still obviously works.

So, if you know what resolution you need, give a similar manual edit a try; it may just work for you too.

---


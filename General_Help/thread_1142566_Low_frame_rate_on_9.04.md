---
title: "Low frame rate on 9.04"
date: 2009-04-29
forum: General Help
---

### Post by Berserker v7 on 2009-04-29
Hey all,

I installed Ubuntu 9.04 yesterday, and I think the frame rate is too low. Minimizing, maximizing, opening and closing the windows, or changing workspace, etc. give crappy images all over. I have an Intel 945 board with on-board graphics card and 1GB RAM, and had no issues with my previously installed 8.10.

So, anyone know how to increase the frame rate? or possibly some other solution? thanks...

---

### Post by Berserker v7 on 2009-04-29
please, somebody help!!!

---

### Post by Nano_ext3 on 2009-04-29
What driver are you using in your /etc/X11/xorg.conf file?

---

### Post by Berserker v7 on 2009-04-29
> **Nano_ext3 said:**
> What driver are you using in your /etc/X11/xorg.conf file?

[qoute]Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/qoute]

I had the same settings working for 8.10.

---

### Post by pebo on 2009-04-29
Known problem for many of us with Intel graphics. See [this]("http://ubuntuforums.org/showthread.php?t=1136738") and [this]("http://ubuntuforums.org/showthread.php?t=1130582"), either one may help. Also look in the [wiki]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance") for an explanation.

---


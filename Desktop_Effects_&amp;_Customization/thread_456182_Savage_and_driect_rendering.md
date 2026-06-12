---
title: "Savage and driect rendering"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by numbers1thru9 on 2007-05-27
I have an IBM T23 that I just installed Feisty Fawn on and I am having trouble getting direct rendering set up on. I have found a few guides but nothing has helped. Does anyone know of a guide that will actually help me or anyone know how to get it to work?

---

### Post by bapoumba on 2007-05-27
Hello,

First off, I am not very video-and-such-stuff savvy.

I have an old savage card:
```
~$ lspci |grep ProSavage
00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133]
01:00.0 VGA compatible controller: S3 Inc. 86C380 [ProSavageDDR K4M266] (rev 02)

```
Running **sudo dpkg-reconfigure xserver-xorg**, the savage driver was picked up, and direct rendering set up automatically.
```
~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

This is part of /etc/X11/xorg.conf relevant to video driver:
```
Section "Device"
        Identifier      "S3 Inc. 86C380 [ProSavageDDR K4M266]"
        Driver          "savage"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C380 [ProSavageDDR K4M266]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"

```

Hope this helps.

---

### Post by Talon2 on 2007-05-28
See this bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905)

You might want to add your own comments.  This bug is shown as a LOW priority.  I can't say that I agree.

---


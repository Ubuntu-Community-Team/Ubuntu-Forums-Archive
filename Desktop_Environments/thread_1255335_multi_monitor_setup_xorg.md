---
title: "multi monitor setup xorg"
date: 2009-09-01
forum: Desktop Environments
---

### Post by astbis on 2009-09-01
Hi forum

I am trying to get a multi monitor setup to work on my IBM T42p. Every howto i find looks like what i have done. What is wrong, what am i missing.
I was able to do it a long time ago on Gentoo, but now nothing seams to help.

Ubuntu: jaunty

Appreciate every help.

My [Xorg.0.log at pastebin]("http://pastebin.com/m4a8810f0")

```

Section "Monitor"
    Identifier     "Monitor1"
    HorizSync       28-49
    VertRefresh     43-72
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device1"
    BusID          "PCI:1:0:0"
    Screen         0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Screen1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050"
    EndSubSection
EndSection

Section "Monitor"
        Identifier   "Monitor2"
        Option       "DPMS"
EndSection

Section "Device"
    Identifier     "Device2"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
       Identifier "Screen2"
       Device     "Device2"
       Monitor    "Monitor2"
       DefaultDepth     24
       SubSection "Display"
               Depth     24
               Modes    "1680x1050"
       EndSubSection
EndSection

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Screen1" 0 0
        Screen      1  "Screen2" LeftOf "Screen1"
EndSection

```

Regards, Dennis

---

### Post by llcawthorne on 2009-09-03
I'm no expert on these things, but shouldn't the Device line under "Screen1" read "Device1" instead of "Screen1"?

---


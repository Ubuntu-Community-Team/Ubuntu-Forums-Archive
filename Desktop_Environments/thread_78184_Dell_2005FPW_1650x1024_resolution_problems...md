---
title: "Dell 2005FPW 1650x1024 resolution problems.."
date: 2005-10-17
forum: Desktop Environments
---

### Post by devolut on 2005-10-17
I am sure there aren't too many people with this problem but I might as well start somewhere.  Recently installed BB and also recently bought this monitor w/ native resolution of 1650x1024.

Being somewhat new to X I just edited /etc/X11/xorg.conf and added "1650x1024" to the appropriate line for my colour depth.  When X loads, it hits the resolution but on the right side of the screen is a column of pink pixels.. wondering if anyone's used this monitor or had any luck, or if you can offer any suggestions.  Maybe the driver for the video card needs to go?

---

### Post by mangoshake on 2005-10-18
don't know if that is what the problem is, but as a fellow Dell 2005FPW owner, I'd like to remind you that the monitor runs natively at **1680x1050**, not 1650x1024.

Here are the relevant sections of my /etc/X11/xorg.conf (running smoothly on 1680x1050 @ 60Hz) :

```

Section "Monitor"
        Identifier      "Dell 2005FPW"
        Option          "DPMS"
        HorizSync       31-83
        VertRefresh     56-75
        Modeline        "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
        Monitor         "Dell 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection

        ...

        SubSection "Display"
                Depth           24
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

The modeline under the monitor section was generated with [this modeline calculator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") using the specs found on [AnandTech]("http://www.anandtech.com/displays/showdoc.aspx?i=2400&p=2")

Reference:
[Widescreen LCDs and Ubuntu Linux]("http://64.233.161.104/search?q=cache%3Ahttp%3A%2F%2Fwww.wiredfool.com%2F2005%2F06%2F15%2FwidescreenLcdsAndUbuntuLinux")

---

### Post by devolut on 2005-10-18
DOH.  That was entirely the problem.  Thank you very much for this.

---

### Post by 5hundy on 2005-10-18
For whatever reason that modeline didn't work for me, however this worked:
```

ModeLine        "1680x1050" 119.0 1680 1728 1760 1840 1050 1053 1059 1080

```

---


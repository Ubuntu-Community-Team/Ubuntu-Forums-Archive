---
title: "Dual Monitor on Ubuntu Doubts"
date: 2007-09-17
forum: Desktop Environments
---

### Post by FFighter on 2007-09-17
Hello all,

I've some questions about Ubuntu's support for multiple monitors and I would be grateful if someone could help me.

**Firstly** - my main monitor is a LG Flatron L1753T LCD - its default res is 1280x1024 - 60hz freq. I've noted that in the xorg.conf file, the screen that corresponds to this monitor has the following configuration:

> 
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
   ** Option         "metamodes" "CRT-0: 1280x1024_60 +1280+0, CRT-1: 1280x1024_75 +0+0"**
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


**The "metamodes" option has CRT in it. Shouldn't it be LCD? Or it doesn't make any difference at all?**

**The second question is:** Is there any application or xorg extension that could add behaviours similar to the ones that the following app does for Windows OS with dual monitors?

> [http://lifehacker.com/software/featured-windows-download/make-the-most-of-multi+monitors-with-ultramon-267254.php](http://lifehacker.com/software/featured-windows-download/make-the-most-of-multi+monitors-with-ultramon-267254.php)

Thanks,

Marcelo.

---

### Post by FFighter on 2007-09-18
No suggestions? :(

---

### Post by Chudilo on 2007-09-18
Install your video driver using ENVY. 
Both NVIDIA and ATI drivers support Dual monitors on ubuntu natively just like in WIndows. 
Ough and there is a Video Driver GUI to set this up just like in Windows.

---

### Post by maybeway36 on 2007-09-18
The new version of Ubuntu out in October will be much better at dual-monitor setups.

---

### Post by FFighter on 2007-09-19
> 
Install your video driver using ENVY.
Both NVIDIA and ATI drivers support Dual monitors on ubuntu natively just like in WIndows.
Ough and there is a Video Driver GUI to set this up just like in Windows.


I already have twin view working and I saw the GUI to configure. The problem is not configuring it, see my questions again.

Thanks.

---

### Post by rsambuca on 2007-09-19
Is the lcd monitor connected via analog or digital connectors?  I can't remember where I read it a while ago, but I seem to recall that crt designation will be used in xorg for analog connections.

---

### Post by FFighter on 2007-09-19
rsambuca, Thanks for the tip. Yeah, the monitor is in "analog mode" which means it is being connected to the video card through a regular 15 pin plug.

---

### Post by rsambuca on 2007-09-19
With regards to the dual display thing, can't you just add another panel to the second display?  You can then just right-click the panel and add the Window List applet.

---


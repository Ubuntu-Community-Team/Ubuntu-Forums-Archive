---
title: "RasterOps Monitor"
date: 2009-10-25
forum: Desktop Environments
---

### Post by boondocks on 2009-10-25
I installed Ubuntu 9.10 Desktop on system with an older RasterOps TX=D2131NMP monitor.
It did not recognize this particular monitor.
Monitor "Unknown" 800x600 60Hz
So I tried ...
System -> Preferences -> Display -> Detect Monitors
and that makes no difference.

This is a great 21-inch monitor and I would like to use a higher resolution.
What should I do?

---

### Post by sohlside on 2009-10-25
If you focus on getting your video card drivers configured you should be able to negate any issues form running a generic monitor.  Have you done that yet?

---

### Post by boondocks on 2009-10-25
No, I have not configured the video card driver for this particular monitor.
I did not have to do this before.
Ubuntu had automatically recognized every monitor that I have used in the past.
This is the first time I have used this older RasterOps TX=D2131NMP monitor.

How should I proceed?

---

### Post by sohlside on 2009-10-25
> **boondocks said:**
> No, I have not configured the video card driver for this particular monitor.
I did not have to do this before.
Ubuntu had automatically recognized every monitor that I have used in the past.
This is the first time I have used this older RasterOps TX=D2131NMP monitor.

How should I proceed?

Switch focus from the monitor to the graphics card/chip instead. I'm very new to Ubuntu myself but my suggestion is to check your repositories for proprietary drivers.  If you have Nvidia or ATI graphics you should be able to see some recommended driver options.  Go with whatever is recommended (will have (Recommended) noted on that driver option).  Display resolution in most all operating systems is reliant upon the drivers for the graphics card/chip rather than the monitor itself.
Also post your xorg.conf file here and maybe someone else will come along who can figure out the exact issue in a more technical manner.
To get your xorg.conf open a terminal and type ```
gedit /etc/X11/xorg.conf
```.  Then copy and paste what you see.

---


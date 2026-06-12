---
title: "ridiculously low resolution"
date: 2009-04-17
forum: Desktop Environments
---

### Post by Apocrathia on 2009-04-17
i don't know what happened, the resolution is too low to do anything (<320x240). here's my /etc/X11/xorg.conf

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

i have an nvidia geforce 5700 in the computer, i would normally use the nvidia-settings app to adjust the display, however, i can't even get to it...

i've tried purging the setting app hoping that it would revert to default settings but nothing.

any ideas??

---

### Post by Apocrathia on 2009-04-18
I've tried resetting my xserver by using ```
sudo dpkg-reconfigure xserver-xorg
``` However, I still haven't had much luck. Thankfully the computer sits in my closet and was configured to run headless server (gui for vnc), I've only recently hooked a monitor to it. But it still performs all the tasks I need for it to.

---

### Post by ambdeep on 2009-04-18
did this happen after an upgrade or someting......if so go to the nvidia site and download the driver and install it....usually that is the main problem.

---

### Post by Apocrathia on 2009-04-18
I switched the monitor port on video card from one to the other, and that's when it freaked the hell out.

can I uninstall everything via the commandline? i have ssh access to the box and that's about the most useful thing available to me right now.

---


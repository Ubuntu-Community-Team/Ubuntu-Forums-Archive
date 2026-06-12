---
title: "xorg crashes with fglrx driver on Dell 13R"
date: 2011-09-10
forum: Desktop Environments
---

### Post by haoniukun on 2011-09-10
Hi all,
I don't know if anyone has the same problem.
After I upgraded my system from 10.10 to 11.04 this May, my XWindows system randomly crashes.
In Ubuntu 10.04 and 10.10, Ubuntu worked perfectly fine which never caused any problem to me.
I'm using Dell 13R. My graphic card is ATI 5470.
Every week, I tried to upgrade my system to the latest one.
But that doesn't help.
If anyone has ever solved the problem, would you please share your experience how to solve the problem?
In fact, my biggest problem is that I can see open web page with flash.
If there is a flash on the web page, the browser, Chrome and Firefox, will crash.
I think if the XWindow problem is solved, this problem can also be solved.
I copied my xorg.conf file. I hope it can also help.
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth    24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Module"
        load "dri"
        load "glx"
EndSection

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection


Thanks and best regards:confused:

---


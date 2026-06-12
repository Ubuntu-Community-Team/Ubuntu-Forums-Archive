---
title: "ATI Radeon HD 4650, fullscreen resolution"
date: 2014-12-14
forum: Gaming &amp; Leisure
---

### Post by maritim on 2014-12-14
Hello everybody,

I have a problem when I try to play games in full screen. To be more specific I upload a screen here: 
[IMG]http://s12.postimg.org/vy0umix8t/Screenshot_from_2014_12_14_13_07_49.png[/IMG]

As you can see, the Unity bars remains on screen. If I hide the left bar, the "fullscreen" game will go a little bit left, but will not fit on the upper bound. This problem exist for almost any application that use OpenGL fullscreen mode (PCSX, almost any game on Steam) but not with Counter Strike 1.6 (I don't know if it matters, but I wanted to be exactly).

For almost two days I tried to search an answer for that.

I have an Acer Aspire 5748ZG with ATI Radeon HD 4650, 1024 MB and I use Ubuntu 14.04. I tried to install drivers for it, I tried almost every suggestion from forums and sites, but nothing works... apparently there is a bigger problem with ATI Drivers on Ubuntu 14.04 (On Ubuntu 12.04 everything works fine, and I understand that in 14.10 it works again). So after I understand that I can't install proprietary drivers, and open source ones doesn't work properly, I tried to understand why some games works on fullscreen and another ones don't, but for this I don't find an answer.

How could I fix the fullscreen mode for other games?

Thank you and have a nice day :)

---

### Post by DanglingPointer on 2014-12-14
How about sticking with 12.04.5?  It has the exact same kernel as 14.04 for the next several months at least.

---

### Post by QIII on 2014-12-14
There is no ATI proprietary driver that will work with that adapter with any release of Ubuntu beyond 12.04.1.   There is no proprietary driver that will work with that adapter and the more recent X Server used since then.

It may be that the open source driver has improved substantially (it has been improving for a couple of years) in more recent releases that you will get satisfactory performance, but the proprietary ATI driver will not work.

To use an ATI proprietary driver with that adapter -- which will NOT be the most recent driver -- 12.04.1 with the driver in the 12.04.1 repository will be the only way.

---

### Post by maritim on 2014-12-17
Yes,  I understand that... I'll probably try 12.04 cause with it I don't had these problems. Maybe I will keep both of them, 12.04 mostly for gaming cause I really don't want to try to integrate Windows now.

Thank you for answers guys, hope that AMD will try to create drivers for Unix in the near future.

Have a nice day :)

---

### Post by QIII on 2014-12-17
There are ATI drivers for Linux.

Just not any that will work with those older models of adapters in Linux distros that use newer versions of X Server.

And that's not going to change...

---

### Post by Bashing-om on 2014-12-17
maritim; Hi !

To get 12.04.[color=green]1[/color]
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

Make sure you choose the release architecture in the .1 series . And do not accept any option to enable/upgrade HWE  (Hardware stack Enablement); As that upgrades the Xserver out of range of your video card. HWE is only an option and is not required. It is there to support new hardware.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---


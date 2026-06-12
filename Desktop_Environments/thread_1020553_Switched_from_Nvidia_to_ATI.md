---
title: "Switched from Nvidia to ATI"
date: 2008-12-24
forum: Desktop Environments
---

### Post by warped6 on 2008-12-24
After I upgraded my desktop to 8.10 from 8.04 I had issues with the Nvidia drivers and dual monitors. After fighting it for a weekend it seems like the drivers were just broken so I switched to an ATI card. This proved to be a pain in the backside too but I did get it running.

After a month I decided I wanted some eye candy so I tried to enable compiz. It complains about missing driver, so I ran compiz-check. Here is what I got...

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV670PRO [Radeon HD 3850]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems.../usr/bin/fglrxinfo: error while loading shared libraries: libGLcore.so.1: cannot open shared object file: No such file or directory
/usr/bin/fglrxinfo: error while loading shared libraries: libGLcore.so.1: cannot open shared object file: No such file or directory
           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use. 

I saw that line about libGLcore.so.1. It rang a bell. Yeah I see the same thing when I boot. It flashes by saying FAIL can't find it.

Is that something left over from the Nvidia drivers? Seems like most posts about libGLcore.so.1 are connected to Nvidia somehow.

I tried running envyng to remove the NVIDIA drivers. That confused things for a bit, so I ran it again and installed the ATI drivers and things are back to the way they were.

So how do I get rid of that error and get compiz to work.

Thanks,
Mike

---

### Post by warped6 on 2008-12-31
Well to answer my own post. I tried everything I could find but had no luck. The computer ended dying due to other problems so did a fresh install and things are ok now.

---

### Post by Rohan Kapoor on 2009-01-01
> **warped6 said:**
> Well to answer my own post. I tried everything I could find but had no luck. The computer ended dying due to other problems so did a fresh install and things are ok now.
Ok then!

Some information that I have deduced throughout my testing:

EnvyNG *hates* ATI/AMD in 8.10.

Switching graphic card manufactures on a running system normally causes ***A LOT*** of problems.

---

### Post by warped6 on 2009-01-01
Yeah I've noticed that about switching graphic card companies. Ouch. Ah well, live and learn.

It seems like I could never fully get rid of the Nvidia drivers. I could still see them loading when the system came up. :rolleyes:

> **darth-vader said:**
> Ok then!

Some information that I have deduced throughout my testing:

EnvyNG *hates* ATI/AMD in 8.10.

Switching graphic card manufactures on a running system normally causes ***A LOT*** of problems.

---

### Post by Rohan Kapoor on 2009-01-01
> **warped6 said:**
> Yeah I've noticed that about switching graphic card companies. Ouch. Ah well, live and learn.

It seems like I could never fully get rid of the Nvidia drivers. I could still see them loading when the system came up. :rolleyes:
Just some further information you might be interested in:

Nvidia makes much better graphics drivers for Linux!

---

### Post by warped6 on 2009-01-02
> **darth-vader said:**
> Just some further information you might be interested in:

Nvidia makes much better graphics drivers for Linux!


Yeah I agree but for whatever reason I could not get dual head + compwiz to work with the Nvidia card I had after upgrading to 8.10. After a lot of poking around, seems like there was a bug in the drivers. So I switched. It's all working now which is the important point. So it goes.

---

### Post by Skripka on 2009-01-02
> **darth-vader said:**
> Just some further information you might be interested in:

Nvidia makes much better graphics drivers for Linux!

I like Nvidia Linux drivers better than Nvidia Windows drivers, actually.


ATi has a LONG history of terrible drivers...on Windows they have finally shaped up, their linux drivers are still primitive and a joke in comparison.  With ATi opensourcing their drivers though-hopefully that'll change.  ATi makes great cards-it's far past time their drivers were a match for their cards.

---

### Post by CHaoSlayeR on 2009-01-09
Hi there,

the only thing that I can say is that nVidia is not an option for me anymore. I have a notebook with an nVidia Geforce FX 5200 Go 64M and I'm one of the many that suffered from the more than bad KDE4 performance problems. Currently I'm using the xserver-xorg-video-nv driver which works fine with KDE4 excluding the fancy effects and dual head don't want to work somehow. Basically I don't like those proprietary drivers as they screw up the OpenGL-part of the system (that's why installing nvidia driver enforces removing the fglrx and vice versa). At work I have a machine running Ubuntu 8.10 with the radeon open source driver on a Radeon X1350 in dual-head configuration and I get full OpenGL hardware support (all KDE4 effects working, glxgears runs at around 2500 FPS). I've never seen anything like that with either the nv or the nouveau driver (although the nouveau folks are working on that part).

In addition I like the fact that ATI was bought by AMD because AMD is the one that demands Linux support for their products and taking this into account everyone can see that nVidia is a lot longer at the linux side. This is why nVidia drivers seem to work better, there are just more workarounds builtin. That said and the additional fact that AMD/ATI is slowly turning internal knowlegde into open source (e.g. the stream sdk, working on OpenCL support, providing first OpenGL details for RV7xx cards) it is giving way more back to the community than nvidia does.

C]-[aoZ

---


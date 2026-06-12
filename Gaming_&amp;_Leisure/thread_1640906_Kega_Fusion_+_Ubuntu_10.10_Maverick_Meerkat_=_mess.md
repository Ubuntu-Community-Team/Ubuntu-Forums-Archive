---
title: "Kega Fusion + Ubuntu 10.10 Maverick Meerkat = messed up colors"
date: 2010-12-08
forum: Gaming &amp; Leisure
---

### Post by Jun-01 on 2010-12-08
I installed the latest version of Ubuntu, the 10.10, yesterday. For the first time my laptop's ATI Mobility Radeon HD 2400 worked just fine (compiz and vsync enabled, and even extended desktop) with the default, opensource drivers.

Then I tried to run Kega Fusion 3.63x, and got messed up colors in the games. Other Emulators like Zsnes and Nestopia ran just fine. Tried 3.62x with no success either.

Has any other ATI Mobility Radeon user got the same results? Is there any workaround, or am I going to be forced to install ATI's buggy fglrx driver in order to run Kega Fusion properly? Though I don't know if it's an incompatibility with the new version of Ubuntu, or with the opensource display drivers (or perhaps both of them).

I tried to use the Gens/GS emulator instead, but didn't like it. It doesn't correct the aspect ratio when switching to fullscreen mode.


[[IMG]http://img802.imageshack.us/img802/3696/screenshot2a.th.png[/IMG]]("http://img802.imageshack.us/i/screenshot2a.png/")

[[IMG]http://img199.imageshack.us/img199/5578/screenshotkxl.th.png[/IMG]]("http://img199.imageshack.us/i/screenshotkxl.png/")

---

### Post by Jun-01 on 2011-06-22
Since nobody replied since I posted this thread, I decided to update it with what I've found out in the last months.

Apparently the open-source radeon drivers have issues with OpenGL acceleration. Not only I got messed-up colors in Kega Fusion, I got framerate issues when playing in fullscreen mode with ZSNES and Gens as well. When I installed the private drivers from AMD for test purposes, Vsync for the desktop became a thing of the past, but Kega Fusion and the other emulators worked without the issues I got when using radeon.

So far it seems that the open-source radeon drivers till now are at least good enough to work with compiz and play videos.

---


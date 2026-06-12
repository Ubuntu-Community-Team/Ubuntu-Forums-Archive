---
title: "XGL, Beryl + Google Earth on ATI 200M"
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by scradock on 2007-05-24
I've been trying to see if I can get Google Earth to run on Feisty with XGL and Beryl as Window manager. The ATI Radeon Xpress 200M card needs the fglrx drivers - I'm using the ATI proprietary version 8.36.... They don't "do" composite extension, so I can't enable cool Desktop Effects without using XGL (or AIGLX, but I haven't gone that way, because it needs the open source Radeon drivers, I believe.)

Loading XGL in a session or running an XGL session "breaks" Google Earth. It starts to initialize, then hangs and has to be forced to quit. Without XGL, Google earth runs fine. With XGL, choosing metacity or Beryl as window manager leads to the same failure to initialize. But everything else about XGL and Beryl work - cool emerald themes and desktop cube/polygonal prism.....

The suggested solution (from one of the Google Earth forum threads) was to put a copy of "libGL.so.1" from the 8.27... ati fglrx drivers in the G-E folder. This gets past the initializing stage, but the globe and the maps are drawn without images - not a lot of point....... The roads, rivers, city names and borders show up fine, on a white background. Again, same behavior with metacity or Beryl as window manager.

Last thing I've tried - I took the libGL.so.1.2.xlibmesa file from /usr/lib/fglrx and popped it into the Google Earth folder, renamed as "libGL.so.1". Now G-E loads, runs and displays maps. It's slow to render, and it loses some letters of the text (city names, etc). But it's there!!!!!

Anyone got any further? There should be a version of the driver that does it all - or is someone working at making one??????

---

### Post by thered on 2007-12-02
[I]
Last thing I've tried - I took the libGL.so.1.2.xlibmesa file from /usr/lib/fglrx and popped it into the Google Earth folder, renamed as "libGL.so.1". Now G-E loads, runs and displays maps. It's slow to render, and it loses some letters of the text (city names, etc). But it's there!!!!![/I]

The above worked for me.  I had a perfectly good installation which yesterday took to hanging at the initialization stage (hadn't used it for a month or so).  Un-installed and re-installed but to no avail.

Was going to start new thread but found this, luckily - it is now resolved.  I don't seem to have a problem with text or speed of rendering.

I have a DEll inspiron with 256 Radeon 1400x

Cheers scradock :)

---

### Post by bobpress on 2007-12-09
I had the problem that Google Earth would freeze on initialization.  I have an ATI Xpress 1100 with Beryl turned on.  I downloaded the libGL.so.1.2 from [here]("http://pathfinder.homelinux.net/libGL.so.1.2") and renamed it to libGL.so.1.  It needs to be moved to your google earth directory which should be /home/[your user name]/google-earth.

---

### Post by nikoPSK on 2007-12-09
ty bob.

---

### Post by jellyturtle on 2008-01-25
Yay! This worked perfect for me. The graphics are a bit chunky, but that could be my lowly Radeon Xpress 200 graphics card. Thank you!

---

### Post by SIXAXIS on 2008-02-12
Quick question for you guys with the ATI Radeon 200M, how do you enable XGL without it being extremely slow? I want to have desktop effects but I can't, even when I do enable XGL. So is it possible to enable XGL, have compiz-fusion, and have the computer run fast at the same time?

---


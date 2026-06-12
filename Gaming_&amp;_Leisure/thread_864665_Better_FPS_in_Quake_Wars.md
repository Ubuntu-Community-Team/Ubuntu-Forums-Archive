---
title: "Better FPS in Quake Wars"
date: 2008-07-19
forum: Gaming &amp; Leisure
---

### Post by Tumpster on 2008-07-19
Hey there, I have settings at 1400x900 Wide screen and quality high but I seem to only average 30FPS. My specs are as follows:
Amd Opteron 143 Dual Core Processor
2gb Ram
XFX GeForce 8600 GT XXX 256mb
80GB Main Drive
500 GB External (Seagate Free Agent/Storage)

Anything I can do to improve fps while maintaining my settings? Or am I do something wrong in regards to not optimizing something or selecting something in game? Any advice is appreciated! Thanks!! :)

---

### Post by Perfect Storm on 2008-07-20
Well, if you havn't done it. Disable compiz-fusion will get you some FPS.
Also see if it helps to disable other applications that might be running in the background, you can do that with an application like "BUM" (it's in the repo). Just don't diasble something vitale ;)

---

### Post by Tumpster on 2008-07-20
Thanks!

---

### Post by boktor on 2008-07-20
lol it just sounds like you just haven't uncapped the fps. ETQW's default settings have your fps capped at 30. Bring up the console in-game and type in com_unlockFPS 1.

---

### Post by Tumpster on 2009-04-27
> **boktor said:**
> lol it just sounds like you just haven't uncapped the fps. ETQW's default settings have your fps capped at 30. Bring up the console in-game and type in com_unlockFPS 1.

I'll give this a try but I was also wondering, this "r_useThreadedRenderer 2" that I could use to utilize my dual core setup, I keep getting two different errors. One is "Render Threading is not supported in this build" and "r_useThreadedRenderer is read only." How can I fix that so I can turn it on as I see it's currently set to "0"?

---

### Post by Brebs on 2009-04-27
> **Tumpster said:**
> Render Threading is not supported in this build
Run the [correct executable](http://www.wolfstuff.org/modules.php?name=Content&pa=showpage&pid=16).

> To start the client, use:

etqw

To start the client with renderer threading support, use:

etqw-rthread

---

### Post by Tumpster on 2009-05-10
> **Brebs said:**
> Run the [correct executable](http://www.wolfstuff.org/modules.php?name=Content&pa=showpage&pid=16).

So I followed that and tried to open ETQW via "etqw-rthread.x86" and it does nothing, however when I double click "etqw-rthread" next to it and tell it to run in the terminal it runs just fine and I do improve on the FPS. Is there any way I can create a link in my menu drop down to run this version that works even though it shows it needs to be run through the terminal?


DISREGARD, I got it....

---


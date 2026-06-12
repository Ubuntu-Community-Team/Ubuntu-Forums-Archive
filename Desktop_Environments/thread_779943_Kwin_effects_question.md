---
title: "Kwin effects question"
date: 2008-05-03
forum: Desktop Environments
---

### Post by mirons on 2008-05-03
hi everybody. I've been using compiz some time ago but now that now I've switched to kde4 I'd like to use native effects. I still have XGL enabled, but is it useful? Things doesn't seem to work fine with it but I don't know exactly what conf file to edit in order to disable it and what to load instead of it. So the question is: what infrastructure does kde4 use to render his dektop effects?
(Ps: I've an nVidia card)
Thanks for your help.

---

### Post by luisromangz on 2008-05-03
Using an Nvidia card you should be using AIGLX, and it should be enabled by default in a modern version of Ubuntu.

---

### Post by Zorael on 2008-05-03
You don't want xserver-xgl if you have an Nvidia card, so get rid of that package.

To answer your question, KDE is using its own compositioner, and as such the settings "should" be configurable through the system settings app. KDE4 is (opinion) largely unfinished at present, so the developers may just not have gotten around to adding the configuration part yet, though that seems unlikely.

---

### Post by luisromangz on 2008-05-03
The integrated desktop effects in KDE4 have their settings panel avalaible from the system settings app.

---

### Post by mirons on 2008-05-04
That's all right folks: I have a wonderful GUI where I just have to thick the effects I want the trouble is just a few works, and they works just using xrender as infrastructure (no OpenGL). I suppose using OpenGL I should have more effects, but it doesnt work... using the command glxinfo I discovered I have also no direct rendering... (could be this the problem??)

P.S. you can look @ my xorg.conf, is attached. I messed up all day with it and it still doesn't work....

---


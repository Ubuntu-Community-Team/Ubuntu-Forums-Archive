---
title: "ZSNES Studdering sound blinking &quot;No application is currently playing or recording au"
date: 2009-12-24
forum: Gaming &amp; Leisure
---

### Post by MrTripi on 2009-12-24
Ok, so I've had similiar issues with snes9x.  The sound will stutter non stop, however I just went to sound preferences and when I click applications I notice that zsnes is constantly flickering.

So I actually see "Alsa Plugin [zsnes]" with a bar to adjust the audio, however it will flicker very rapidly.   Each time it disappears I read "No Application is currently playing or recording Audio".  

Are these two issues related?  I'm currently running Ubuntu 9.10 on an Inspiron 1520 dell laptop.

---

### Post by MrTripi on 2010-01-06
wow, so I take it this is a unique issue.

---

### Post by Grishka on 2010-01-06
umm, I think I've seen this before. guess this may be an issue with pulseaudio. perhaps removing it from your system will help.

---

### Post by MrTripi on 2010-01-06
> **Grishka said:**
> umm, I think I've seen this before. guess this may be an issue with pulseaudio. perhaps removing it from your system will help.

If I remove it then my laptop loses duplex audio output support.  Are there any alternatives?

---

### Post by Grishka on 2010-01-06
see if [this](apt:libsdl1.2debian-all) helps.

---

### Post by MrTripi on 2010-01-06
> **Grishka said:**
> see if [this](apt:libsdl1.2debian-all) helps.

Same problem.  The application will continue to flicker under sound manager.  

Every now and then when it stops flickering, the sound becomes clear but that usually lasts about 1-2 seconds.  

It's odd

---

### Post by Grishka on 2010-01-06
yea, I'm positive that this is an issue with pulseaudio, curse it. if you can't live without it, then I see no hope for you. unless you manage to disable it while using zsnes, somehow. unfortunately, simple solutions like 'killall pulseaudio' won't work in the long run with karmic. I remember seeing a script somewhere on these forums to disable it temporarily, maybe it'll work for you, should you manage to find it. gl.

---

### Post by MrTripi on 2010-01-06
> **Grishka said:**
> yea, I'm positive that this is an issue with pulseaudio, curse it. if you can't live without it, then I see no hope for you. unless you manage to disable it while using zsnes, somehow. unfortunately, simple solutions like 'killall pulseaudio' won't work in the long run with karmic. I remember seeing a script somewhere on these forums to disable it temporarily, maybe it'll work for you, should you manage to find it. gl.

Are there any alternatives to pulseaudio which provide the same functionality?  

Honestly, duplex support is the only reason why I even use it.

---

### Post by Grishka on 2010-01-06
> **MrTripi said:**
> Are there any alternatives to pulseaudio which provide the same functionality?  

Honestly, duplex support is the only reason why I even use it.

ALSA supports full duplex as well, there should be no need to use PA for that at all. if you have some serious music-making in mind, use JACK. neither PA nor ALSA alone will cut it, in this case.

---

### Post by MrTripi on 2010-01-06
> **Grishka said:**
> ALSA supports full duplex as well, there should be no need to use PA for that at all. if you have some serious music-making in mind, use JACK. neither PA nor ALSA alone will cut it, in this case.

I think I may be confusing the terminology. A while back, using one of the older Ubuntu versions I remember there was a common issue with running multiple audio applications under certain hardware.  Basically, you'd only hear audio from one application(flash was a major problem)

I have an Dell Inspiron 1520, apparently it doesn't have the hardware necessary to accomplish this so it's done on the software layer.  

Pulse Audio provided a feature which corrected this, I assumed it was DUPLEX Audio output which allowed Pulseaudio to "splice" the audio from multiple applications together.  

It works great, just in this instance...it sucks.  Are there any alternatives?

---

### Post by MrTripi on 2010-01-06
nevermind, I found a solution

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1306356](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1306356)

"autospawn = no" in the pulseaudio config and "pasuspender" = win :popcorn:

---

### Post by MrTripi on 2010-01-06
actually don't kill the autospawn.  It causes problems, pasuspender is all you need

---


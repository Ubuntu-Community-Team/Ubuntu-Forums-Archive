---
title: "Beryl kill my videos ?"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by nqsonk9 on 2007-06-10
Hi guys,
I've Beryl 2.0 installed in my Feisty with ATI 128MB card. Everything works fine except for the lags I get in my video player
Each time I enable Beryl, my video player just show black screen when the audio still plays.

Any suggestion ?
Help, pls :'(

---

### Post by BeardlessForeigner on 2007-06-11
In VLC media player if I make the output mode X11, that lets me play with beryl on but i usually just use the default settings and switch to metacity from beryl settings manager since thiis seems to give me better video. Also, I have an ATI X300 and when i had XGL instead of AIGLX my video playback was terrible (flashing diagonal line during playback).

---

### Post by reacocard on 2007-06-11
You have to change the display driver used by your player. Xshm is best, but uses a lot of CPU. Xvideo usually works pretty well, and is much easier on your processor. Don't even try the OpenGL driver, it won't work.

---


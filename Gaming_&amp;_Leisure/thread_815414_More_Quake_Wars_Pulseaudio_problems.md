---
title: "More Quake Wars Pulseaudio problems"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by djscantron on 2008-06-01
I'm running a fresh install of 8.04 i386 here, I downloaded the 1.5 installer and everything ran fine. I had sound in quake wars, urban terror, nexuiz, and neverball.

Now I have sound in none of them.

I didn't edit any config files. I've never even opened a terminal, except to install quake wars.

How do I get my games to run with sound under pulseaudio, with other application at the same time. I want to be able to listen to music.

---

### Post by djscantron on 2008-06-01
Heres the console output:

------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.15
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: No such file or directory
dlclose
WARNING: sound subsystem disabled


BTW, this is the third install of hardy I've done, because every time, after a few days, the sound on my games stops working.

Why does it keep breaking?

---

### Post by twright on 2008-06-01
you can disable pulseaudio by selecting alsa for everything in /system/preferences/sound and the restarting

---

### Post by azendal on 2009-10-30
I found a solution on:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/372843](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/372843)
seems that installing libsdl1.2debian-pulseaudio
this will remove libsdl1.2debian-alsa
and this solves the problem for UrbanTerror a Quake based Game, also in that thread
they report this worked for them on other games

---


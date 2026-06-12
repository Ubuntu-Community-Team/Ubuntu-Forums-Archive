---
title: "Weird doom3 sound problem"
date: 2010-12-13
forum: Gaming &amp; Leisure
---

### Post by psycho5 on 2010-12-13
Hi, I installed doom3, everything works fine, except the sound starts lagging behind the video. It does not skip or anything, it just delays itself after a change of scene, for example, entering the first door to pick up the pda and stuff. The sound goes off, then comes back on, playing back all the actions sounds that should be sync'd  *10-15 seconds after* with what that I did just then, if you understand.

I tried the sound troubleshooter tip, but it didn't work. Doom3 auto detects sound as Best,  not alsa or oss. (in the doom3 game settings for sound).

Anyone else have this issue? Any help would be appreciated.

Running 10.10, 32-bit.

---

### Post by alexandrius on 2010-12-14
Damn, i'm not at home now, therefore i can't send you that small string which must be added to doom3 executable file, if nobody replys i can reply later :)

---

### Post by Soulcage on 2010-12-14
doom3 +set s_alsa_pcm plughw:0 +set s_driver alsa +set NumberOfSpeakers 2

This works for quake 4, enemy territory quake wars, and doom 3.
You can change these settings in game then restart or in the config file or when you launch in a terminal.
Idk if you need the NumberOfSpeakers one since I didn't change mine.

---


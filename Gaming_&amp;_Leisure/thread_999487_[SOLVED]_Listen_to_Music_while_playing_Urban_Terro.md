---
title: "[SOLVED] Listen to Music while playing Urban Terror"
date: 2008-12-01
forum: Gaming &amp; Leisure
---

### Post by juanoleso on 2008-12-01
I would like to listen to music while playing urban terror, but if I have rhythmbox or VLC open and playing a song while I start Urban Terror the UrT console says:

```
------ Initializing Sound ------
Initializing SDL audio driver...
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
SDL audio driver is "(UNKNOWN)".
SDL_OpenAudio() failed: No available audio device
Sound initialization failed.
```

No Sound in UrT only music.

Otherwise it says:

```
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  470
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x8b87610 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started

```

Opening UrT and then Media Player gets opposite results...

Am i missing something?  Any suggestions?

thanx.


Edit: Looking through this thread,[[HOWTO] SDL sound (read: ALSA) support for Enemy Territory]("http://ubuntuforums.org/showthread.php?t=362231&page=12"), but I don't think his script supports the free ioUrbanTerror (or I didn't look through the script enough or I don't know enough about scripting).

---

### Post by juanoleso on 2008-12-03
Bump

Could this possible be a program limitation?

I'm looking at the Urban Terror forums as well.  Will probably ask over there.

---

### Post by detrate on 2008-12-03
I'm not really familiar with UrT's engine but it sounds like it can be a sound lib conflict.  Make sure your media player and UrT are both using the same sound lib, be it ALSA, pulseaudio or whatever.

---

### Post by binarymutant on 2008-12-03
idk about rhythmbox but UrT works well with audacious

---

### Post by juanoleso on 2008-12-03
Thanks you guys.  It turned out to be a sound driver conflict.  I used the gnome "Sound" GUI under preferences and set music from Autodetect to ALSA and now I have UrT effects with Rhythmbox music.

---

### Post by detrate on 2008-12-03
happy it worked out for you

---


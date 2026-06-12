---
title: "Sound distortion/popping with Amarok"
date: 2009-11-16
forum: Desktop Environments
---

### Post by Melcar on 2009-11-16
I'm getting some really awful sound distortion/popping with Amarok when playing mp3.  No other application does this (Dragon, Audacious, Audacity, SMplayer).  I'm not using PA just plain Alsa and whatever Kubuntu Karmic uses as a sound server.  Anyone having similar problems with Amarok?  Is there a way to fix it other than installing another music player?

---

### Post by Zorael on 2009-11-17
> **Melcar said:**
> whatever Kubuntu Karmic uses as a sound server.
That would be none at all; Phonon (contrary to popular misconception) is just an abstraction layer ontop of the sound API of choice (ALSA, OSS, Pulse, ...).

I can't say much than WFM. I take it it's not the HDA power saving pops you mean (upon playing sound after 10+ seconds of inactivity), but pops throughout songs?

---

### Post by schnelle on 2009-11-17
I am using PulseAudio in Amarok, Audacious and SMPlayer and everything works just fine. Maybe you should try PulseAudio.

---

### Post by Melcar on 2009-11-17
Tried PA; no go.  Only Amarok does this.  I've been playing music with Juk and Qmmps and sound is crystal clear. Other media players are unaffected also.  Popping sound and loud distortion (like when you crank up the volume and your speakers can't handle it).

---


---
title: "sounds issue: everything sounds downsampled into oblivion"
date: 2005-09-04
forum: Gaming &amp; Leisure
---

### Post by sander marechal on 2005-09-04
Hello,

I have tried most of what is written in [this sticky about sound issues](http://ubuntuforums.org/showthread.php?t=42492) but I keep haviong sound troubles. All of the games I tried so far sound like they are downsampled into nothingness and played over an old internal PC speaker. That has happened on all Hoary installations I tried so far. Games that I know are affected:

- Doom 3 (demo)
- Quake 2
- Cube
- various simpler GPL'ed linux games (TuxRacer et. al.)

The Doom 3 demo has the courtesy to spawn some error messages about it. Here\s an excerpt. This just repeats all the time:

```

idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048

```

Googling for it came up zero though. Does anyone have a clue? The internal sounds in Ubuntu do not have this. It's just the games as far as I can figure out.

Thanks in advance!

-- 
Sander

---

### Post by sander marechal on 2005-09-05
Anyone? Please? It's quite hard to play Doom 3 with bad sound because I miss most of the audio cues and the stuff that's been told in audio logs. 

I tried aRts with no effect. I tried the sound section on ubuntuguide with no effect. I installed polyaudio-alsa with no effect (well, with the effect that I no longer need to kill esd before starting doom). The sound just keeps coming out like it was mixed in a bad software mixer and played over an internal PC speaker.

Thanks in advance!

---

### Post by sander marechal on 2005-09-05
Somehow the problem disappeared after I installed Ubuntu 64 instead of regular Ubuntu (I accidentally installed i386 Ubuntu on my new AMD64 box).

---


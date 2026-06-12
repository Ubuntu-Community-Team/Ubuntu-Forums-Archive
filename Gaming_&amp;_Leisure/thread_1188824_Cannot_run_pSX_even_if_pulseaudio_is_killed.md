---
title: "Cannot run pSX even if pulseaudio is killed"
date: 2009-06-16
forum: Gaming &amp; Leisure
---

### Post by Inquisitorthemad on 2009-06-16
I am trying to run the pSX emulator on this laptop. It worked fine when I was using Ubuntu 9.04 (though I downgraded for hopefully unrelated stability reasons) so it probably isn't the hardware, but when I try to run it - as root or as myself - I get the following:
```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
```

Classically, the solution is to kill Pulseaudio first, and this worked in Jaunty. In Intrepid, however, I instead get the following message, regardless of whether or not I use sudo:
```
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Connection refused'
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted
```

Furthermore, even when I uninstalled PulseAudio from the system outright, I got the latter "connection refused" error message. Nothing I can think of has worked.

Can anyone help me work out what these error messages mean, and what I should do about them?

---

### Post by Inquisitorthemad on 2009-07-15
Bump... Somebody please help...

---

### Post by disturbedite on 2009-07-16
wish i could help. all i can say is that on my opensuse system i only need libpulse installed.

---

### Post by Grishka on 2009-07-17
have you seen [this thread](http://ubuntuforums.org/showthread.php?t=1169703&highlight=psx+sound)?

---


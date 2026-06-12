---
title: "Alien Arena just won't run | Look inside please"
date: 2010-01-21
forum: Gaming &amp; Leisure
---

### Post by alexandrius on 2010-01-21
This is the output:
```
using /home/alex/.alien-arena/data1/ for writing
using /home/alex/.alien-arena/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
AL lib: alsa.c:388: Could not open playback device 'default': Device or resource busy
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy
AL lib: portaudio.c:127: Pa_OpenStream() returned an error: Invalid device
```

---

### Post by Brebs on 2010-01-21
> **alexandrius said:**
> AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy
See what's using ALSA's emulation of OSS, i.e. /dev/dsp:

fuser -v /dev/snd/* /dev/dsp*

---

### Post by alexandrius on 2010-01-22
**Brebs**
First of all thanks for your reply, i forgot to mention that i have completely removed PA and installed alsa instead (on KK)
here is the output from ```
fuser -v /dev/snd/* /dev/dsp*
```

```
alex@alex-desktop:~$ fuser -v /dev/snd/* /dev/dsp*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  alex       1966 F.... mixer_applet2
/dev/dsp:            alex       2025 F.... crx
```

also i just invented that after trying to run Alien Arena audio is missing everywhere!

---

### Post by Perfect Storm on 2010-01-22
check: [http://ubuntuforums.org/showthread.php?t=1375010](http://ubuntuforums.org/showthread.php?t=1375010)

---

### Post by alexandrius on 2010-01-22
**Artificial Intelligence**
I managed to run AA at last, but audio still dies after running the game

heres is what gstreamer-properties says on clicking TEST:
```
ALSA - Advanced Linux Sound Architecture: Could not open audio device for playback. Device is being used by another application
```

I just invented that CRX stays in processes, i have to kill procces to have sound

Thanks no need to reply any more, i fixed by creating document **.alsoftrc** in home directory and adding in the file following code:
```
[general]
drivers=alsa
```

---

### Post by Brebs on 2010-01-22
OpenAL should prefer Pulse, then ALSA, then OSS - in that order. If it prefers OSS instead of ALSA, then I suggest you file a bug report for that silly default in OpenAL.

---


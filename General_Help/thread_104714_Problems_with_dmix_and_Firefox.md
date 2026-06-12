---
title: "Problems with dmix and Firefox"
date: 2005-12-16
forum: General Help
---

### Post by Jormundgand on 2005-12-16
I played a Flash movie (http://video.google.com/videoplay?docid=2889527841583480458) and attempted to play a sound through aplay using dmix and got this:

```
thomas@jabberwocky:~$ aplay -Dplug:dmix /usr/share/sounds/startup.wav &
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
aplay: main:533: audio open error: Device or resource busy
[1] 8796
[1]   Exit 1                  aplay -Dplug:dmix /usr/share/sounds/startup.wav
thomas@jabberwocky:~$ sudo lsof /dev/dsp* /dev/snd/*
Password:
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 8517 thomas   35u   CHR  116,0      7232 /dev/snd/controlC0
firefox-b 8645 thomas   29u   CHR   14,3      7199 /dev/dsp
thomas@jabberwocky:~$
```

Here are the outputs of various commands.

```
thomas@jabberwocky:~$ cat /etc/mozilla-firefox/mozilla-firefoxrc
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
thomas@jabberwocky:~$ cat /etc/asound.conf
pcm.!default {
        type plug
        slave.pcm "dmix0"
}

pcm.dmix0 {
        type dmix
        slave {
                pcm "hw:0,0"
                rate 44100
                channels 2
        }
}

pcm.dsp {
        type plug
        slave.pcm "dmix0"
}
thomas@jabberwocky:~$ cat /etc/environment
LANGUAGE="en_GB:en"
LANG=en_GB.UTF-8
ALSA_OSS_PCM_DEVICE=/dev/dsp
thomas@jabberwocky:~$
```

---


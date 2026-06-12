---
title: "ALSA/OSS config issues?"
date: 2005-12-19
forum: General Help
---

### Post by winter_mute on 2005-12-19
So I switched over to Ubuntu to hopefully fix this issue that I'd been having with some of the other distros, which was that of the audio out feeds.  I'd had a friend recommend Ubuntu, so I gave it a try.  Yet, the problem remains.

What's happening is this:

I start up, say, XMMS and GAIM.  Now, I can hear sounds in GAIM just fine, and I can hear gnome's system noises just fine.  But once I get so far as to try listening to music, I get an error that asks me if I've got my audio out configured correctly.  If I keep pressing play, it'll eventually work.  Now, I prefer fluxbox over gnome, so I switched over to that.  Once I switched over to that, I had no trouble getting XMMS to play on the first try, but if I try chatting with GAIM, or starting any other sort of an audio feed, either the audio can't be heard (even if I stop XMMS), or the program crashes, such as MPlayer does.  Here's the error I get out of MPlayer, if it helps.

> Checking audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
AF_pre: 44100Hz/2ch/s16le
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy


MPlayer interrupted by signal 11 in module: ao2_init
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


---

### Post by jliedeka on 2005-12-19
It may just be a configuration problem.  For Mplayer, check your /etc/mplayer/mplayer.conf file.  The default audio driver should be set to alsa (ao=alsa).  In XMMS, hit control-P for preferences and make sure the output plugin is alsa.  You shouldn't need to use the configuration button.

---

### Post by winter_mute on 2005-12-19
Ah, hey.  Now I can have mplayer and XMMS playing at the same time!  Thanks.  Now I just need to configure the rest of my system to do that.  =P

---


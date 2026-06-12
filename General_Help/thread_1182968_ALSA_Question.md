---
title: "ALSA Question"
date: 2009-06-09
forum: General Help
---

### Post by Ramza500 on 2009-06-09
This is a very generic question:

Is there anyway the ALSA device, /dev/dsp, can be used by more than one process at a time?

I'm running VM Workstation in the background and I need the sound to always be available.  Not to mention when I plug in my webcam it takes over /dev/dsp and won't release it until I unplug my camera.

---

### Post by CatKiller on 2009-06-09
As I understand it, /dev/dsp is the OSS sound device. You can get applications that use OSS to go through ALSA instead by using aoss.

Also as I understand it, you can only use OSS to play sounds from more than one application at once if your sound card supports hardware mixing. Otherwise you can use one of the sound servers that does software mixing, like ESD, artsd, PulseAudio, JACK, or a properly configured ALSA.

---


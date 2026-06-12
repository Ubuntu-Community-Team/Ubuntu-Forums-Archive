---
title: "Warzone 2100 no sound"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by @@@benq@@@ on 2008-05-17
Hello,
first, sorry for my english ;)
I have problem with sound on my ubuntu 64 bit 8.04. I have installed Warzone 2100 from repo and i don't have sound in game. Console shows me this:
```
$ warzone2100 
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
open /dev/[sound/]dsp: No such file or directory
error   : OpenAL Vendor: (null)
error   : OpenAL Version: (null)
error   : OpenAL Renderer: (null)
error   : OpenAL Extensions: (null)
error   : Couldn't open audio device.
error   : Cannot init sound library
```

Game runs great but without sound.

---

### Post by begemot. on 2008-05-27
And i'm trying to launch Glest (3D RTS) on Hardy from official repository, but having this:
```
void Shared::Platform::Window::setStyle(Shared::Platform::WindowStyle) not implemented.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
open /dev/[sound/]dsp: Device or resource busy
OpenAL Vendor: Exception: Couldn't open audio device.
```

Is it because of 8.04 using PulseAudio instead ALSA?

---

### Post by lordcap90 on 2008-07-20
There is a fix for this, it is some thing to do with the pulseaudio not playing nice with the openal. First make sure that you have the pulseaudio esd compatibility layer installed (the package "pulseaudio-esound-compat") and then, as root, edit the .openalrc file in the home directory (just type in "gksudo gedit ~/.openalrc" in a terminal to open it up). then type in this line:

(define devices '(esd))

Worked for all my openal games (warzone, chromium bsu) :D

---


---
title: "No sound in Urban Terror 4 - tried running it in a terminal..."
date: 2007-05-26
forum: Gaming &amp; Leisure
---

### Post by IainT on 2007-05-26
Sound is working fine in other games, inc Padman. In Padman I have to select 'OpenAL' under sound to get sound. No such option I can see in Urban Terror. Ran UrT in a terminal and snipped out the relevant bit (I'm assuming)

```
------ Initializing Sound ------
Initializing SDL audio driver...
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:CMI8738MC6
SDL audio driver is "(UNKNOWN)".
SDL_OpenAudio() failed: No available audio device
Sound initialization failed.
--------------------------------

```

Any ideas gratefully received. Tried several searches, haven't come up with anything so far.

---

### Post by click4851 on 2007-11-29
I have the same problem, I'm using a SB Live! Gamer sound card, the fabled EMUK101(is that right ?) chipset, I've got all mixer sliders on and 75% to max sound. Sound all over the system,  but not in this game.

---


---
title: "Fix for ubuntu's recent audio problems"
date: 2009-12-22
forum: Gaming &amp; Leisure
---

### Post by portets on 2009-12-22
SDL 1.2.14 FIXES ALL OF MY SOUND PROBLEMS!!
i was looking at sdl's release notes and it mentioned: 
[LIST]
[*]     Updated ALSA support to the latest stable API
[*]     ALSA is now preferred over OSS audio.  (SDL_AUDIODRIVER=dsp will restore the previous behavior.)
[*]     Improved support for PulseAudio
[/LIST]
 so i decided to find a ppa with the new package because synaptic doesn't have it.

this means no more workarounds like uninstalling libsdl1.2debian-alsa.
this is a genuine fix at the root of the problem.

_**EVERYTHING IS FIXED FOR ME**_

hopefully this helps everyone else also. here is the ppa i added:
[B]ppa:dnjl/games

[/B]very sorry if this doesn't help others

---


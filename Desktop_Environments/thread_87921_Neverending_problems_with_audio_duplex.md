---
title: "Neverending problems with audio duplex"
date: 2005-11-09
forum: Desktop Environments
---

### Post by suoko on 2005-11-09
Hi,

I'm quite fed up with ubuntu as far as sound is regarded.
I tried applying all howtos about duplex audio / software mixing but up to now I can't keep two audio application running without errors.
Example where I get errors:
- if I open skype it works ok but if I open xmms as well, then I can't receive/make calls with skype because it reports errors with audio (I have to close xmms to let skype work).
- if I open Gizmo then I can't open xmms at all. If I set esd in gstreamer-properties I can open xmms after Gizmo but I get no sound (it looks it's playing with no sound).
- With Gizmo opened or xmms opened, I can't  open audacity/avidemux.
- many others

I tried all possibilities with gstreamer-properties (ALSA, ESD, OSS) and esound server on/off with no success.

Is there a chance by REMOVING esd (I don't care about e event sounds) and only use ALSA? (I tried but I might miss some options)
What about jackd? It should solve all problems, shouldn't it?

I know I only have an ac97 integrated audio card but on THE OTHER OS it works perfectly...

HOWTOS I FOLLOWED:

- HOWTO: Hear multiple sounds using Both ESD & ALSA
- HOWTO: Breezy sounds nice...
- HOWTO: Happy ALSA, OSS, ESD, with Duplex - Sound Settings

---


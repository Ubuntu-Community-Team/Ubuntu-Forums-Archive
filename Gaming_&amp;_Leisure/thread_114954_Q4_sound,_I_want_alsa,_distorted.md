---
title: "Q4 sound, I want alsa, distorted"
date: 2006-01-09
forum: Gaming &amp; Leisure
---

### Post by defuseme2k on 2006-01-09
Before you post, saying this has been covered several times, I already know this.  I am posting because I want the root cause for the problem?  I am running the 64bit version of kubuntu, smp to be more specific.  I had the problems with the alsa and sdl libraries, doing the trick using the /emul/ia32-linux/ extraction, and running ldconfig + double checking /etc/ld.so.conf fixed the game not starting at all.  Once it starts, dear god the sound was horrible.  Sounded like something from the twilight zone.  Switching over to oss half ass sounds ok, I mean it runs okish.  I would much rather be using alsa.  I am using alsa-oss at the moment rather than using the emulation driver.  I saw in adept, that this was the preferred method.

I had seen it suggested that dmix was the problem.  I want to know how to fix this so it works properly, as I know it could and should sound.  There has to be someone that understands the root cause of this :(.

---


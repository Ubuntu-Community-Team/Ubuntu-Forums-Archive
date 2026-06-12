---
title: "Windowed Diablo 2"
date: 2007-05-09
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2007-05-09
Does anyone know the terminal command to run Diablo 2 LOD in windowed mode with everything installed at the default locations in wine?

Also I have no sound ingame, the sound menu is completely disabled, yet I had sound in D2 pre LOD install. Any clues why?

---

### Post by God Of Atheism on 2007-05-10
Add -w to the command.

For the sound, apparently wine 0.9.31 (and later) cause problems. There is a solution to some sound problems in another thread, but that was for people experiencing stuttering sound, not no sound at all, still, it's worth a try.

---

### Post by eilu on 2007-05-16
If you're still stuck on sound- I got sound working on mine by going into **winecfg** and changing the Audio driver from OSS to ALSA. Works great; quality isn't 100%, but that *could* be my tiny laptop speakers.

---


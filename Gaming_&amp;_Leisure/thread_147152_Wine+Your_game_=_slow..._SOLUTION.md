---
title: "Wine+Your game = slow... SOLUTION"
date: 2006-03-19
forum: Gaming &amp; Leisure
---

### Post by Viader on 2006-03-19
Just run winecfg and in audio tab deselect everything except OSS. It will work like a charm :)
I don't know why alsa doesn't work (I get: ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: Nie ma takiego pliku ani katalogu (no such file or directory or something)) and esd i slow like hell. OSS (tm)JUST WORKS(tm) and speedup is... just check it out :)

---


---
title: "Timidity in ScummVM 0.11.1"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by phildaman46 on 2008-07-13
How do you get Timidity to work in ScummVM? I got it to work in dosbox but not ScummVM.

---

### Post by phildaman46 on 2008-07-16
Bump.

---

### Post by Hinrik on 2008-09-18
By making sure that the timidity ALSA sequencer is running (sudo /etc/init.d/timidity start) and having this in your ~/.scummvmrc:

```
[scummvm]
music_driver=alsa
alsa_port=128:0
```

---


---
title: "Ubuntu 9.04 - Choppy Audio in Many Games"
date: 2009-09-15
forum: Gaming &amp; Leisure
---

### Post by rob86 on 2009-09-15
I've noticed that there seems to be a recurring issue with choppy audio in a lot of the games I try. For example, Glest, and Supertuxkart. Supertuxkart always starts with choppy audio, and immediately after the "GO" during a race, the sound stops being choppy, and it works perfectly from then on. It's almost the same with Glest, but more annoying. The choppy audio sometimes starts when the game starts, sometimes the audio begins fine. The audio randomly goes choppy and skips during the game. I don't think it has anything to do with the video, because in both games, the video works fine, it's not slow at all. It's entirely the audio that's the problem.

I thought it was just a problem with these games, but then I started to realize the choppy audio was everywhere, it seems strange, is there something I need to do?

---

### Post by Grishka on 2009-09-17
I'm not sure, but this may be an issue with Pulseaudio. see if this helps. ```
killall pulseaudio
```

---


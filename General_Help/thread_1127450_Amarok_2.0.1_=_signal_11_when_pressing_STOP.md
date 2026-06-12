---
title: "Amarok 2.0.1 = signal 11 when pressing STOP"
date: 2009-04-16
forum: General Help
---

### Post by aurelieng on 2009-04-16
Dear all,

I installed recently Amarok2 on my Kubuntu 8.10 AMD64 box running KDE 4.2.2. It works quite well, but there is a very annoying bug: Most of the time, when the stop button is pressed, its crashes with SIGSEGV. Unfortunately, the KDE crash handler is not able to generate an valid backtrace. I suppose that the phonon-xine backend is used since when I in from a konsole start it, I see

Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"

Any idea / suggestion ?

Cheers,

Aurélien.

---


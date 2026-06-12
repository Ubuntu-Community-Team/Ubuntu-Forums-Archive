---
title: "Moving from 177.82 to 180.22 (Nvidia drivers)"
date: 2009-01-31
forum: General Help
---

### Post by shamusl on 2009-01-31
Does moving from 177.82 to 180.22 offer any improvements in performance? As it is 1080p runs very badly in linux (but just fine in XP) (through VLC), and just wondering if this will improve it at all. And if not, is there another way to improve video playback speed?

My specs:

Graphics Card: 9800 GT
Processor: E6400
Memory 2GB
Hard Drive: 250GB (16 mb cache)

---

### Post by Nepherte on 2009-01-31
The nvidia 180.22 drivers add support for vdpau, something that allows your gpu to decode the video file resulting in less cpu load. That is, if your graphic card supports it, but your card seems rather new. Be aware that vdpau is still in an experimental phase and that you will also need patched video player software (there's a patch for vlc and mplayer).

---


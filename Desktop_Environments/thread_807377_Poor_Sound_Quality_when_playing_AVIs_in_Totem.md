---
title: "Poor Sound Quality when playing AVIs in Totem"
date: 2008-05-25
forum: Desktop Environments
---

### Post by Doughy on 2008-05-25
When I try to play AVI videos using the Totem movie player, the sound quality is really fuzzy and cuts in and out.  I tried opening the same files with MPlayer and the sound is good.

Does anyone know why AVI files might sound bad in Totem, and how to fix?  Thanks.

---

### Post by Doughy on 2008-05-26
I fixed the problem.  I used the synaptic package manager to uninstall the totem-xine package and replaced it by installing totem-gstreamer.

I guess xine and gstreamer are two backend packages for decoding videos/media files, and xine has a bug with some AVI audio.

---


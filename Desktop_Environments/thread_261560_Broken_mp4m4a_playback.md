---
title: "Broken mp4/m4a playback"
date: 2006-09-20
forum: Desktop Environments
---

### Post by anodizer on 2006-09-20
All the gstreamer plugins base/good/bad/ugly are installed, however none of my players using gstreamer can play .m4a files.
I thought dapper's gstreamer 0.10 support those formats, or not?

---

### Post by skymt on 2006-09-20
What players are you using?

---

### Post by anodizer on 2006-09-20
Banshee, Totem-gstreamer and Rhythmbox.

---

### Post by skymt on 2006-09-20
Try installing *libfaad2-0*.

---

### Post by anodizer on 2006-09-20
Hey, thnx!! Actually it was installed, but a crappy repo updated it some time ago causing this problem.

---


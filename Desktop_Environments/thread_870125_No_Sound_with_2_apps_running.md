---
title: "No Sound with 2 apps running"
date: 2008-07-25
forum: Desktop Environments
---

### Post by dontgetshocked on 2008-07-25
Is this normal if I have Movie Player open for Firefox to not be able to play sound because this is what happens to me? Even if I am not playing anything on movie player and just have it open sites such as YouTube wont get any sound.

---

### Post by aullidolunar on 2008-07-25
I had the same problem, I went to my sound properties and gstreamer-properties and change from alsa to pulseaudio, also there's a patch in the repos for the flashplugin-nonfree to use pulseaudio (libflashsupport)

---


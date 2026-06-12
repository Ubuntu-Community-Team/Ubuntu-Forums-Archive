---
title: "sound issue"
date: 2006-03-16
forum: Desktop Environments
---

### Post by sopo_dan on 2006-03-16
well i wouldn't exactly call it a problem, because sound is working
so my issue is: what can i do to be able to hear multiple simultaneous sound sources? for example to hear system sounds while music is playing. because now if i, say, talk on skype and try to play something in xmms i get a device not ready error.

---

### Post by FIONEX on 2006-03-16
If you're using ALSA, it has software mixing enabled, which allows multiple sources to play simultaneously.  The command to get ALSA to mix sound is this for GAIM --> "aplay -D plug:dmix %s".  For xmms, you just have to select ALSA from the sound output menu in preferences.

---


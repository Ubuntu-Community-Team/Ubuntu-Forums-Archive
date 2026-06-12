---
title: "Listen audio player woes"
date: 2006-08-15
forum: Desktop Environments
---

### Post by WhO_KnOwS on 2006-08-15
I wasn't sure weather to post this in the audio forum or here, but I then decided to post it here since it is more of an app problem then a sound-card one.

Whenever I use the Listen audio player some of the other applications (Firefox, aMSN...) can't play sounds anymore. The same doesn't happen if I use a different audio player (xmms, totem). I can even listen to Listen AND totem at the same time.

So what I'd like to know is if it is possible to somehow preven Listen from hijacking whatever part of the sound system it hijacks.

---

### Post by louis_nichols on 2006-08-15
Go into the settings or preferences menu and see whether it has an option to choose from different sound outputs. If you find it, make sure it's set to alsa, not oss.

---

### Post by orb9220 on 2006-08-15
Yes from what I read oss only allows one device at a time I believe.

---

### Post by WhO_KnOwS on 2006-08-15
No such setting exists in the preferences...
Unfortunately, looking at the config file in ~/home/user/.listen revealed to variable or anything connected to either oss or alsa.

---


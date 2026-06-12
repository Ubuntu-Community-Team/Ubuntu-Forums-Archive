---
title: "Doom 3 sound issue with pulseaudio"
date: 2007-03-25
forum: Gaming &amp; Leisure
---

### Post by MaX on 2007-03-25
I had Doom set to OSS and I got no sound, I changed it to ALSA and now it won't start...

So whats up, how do I fix it so that pulseaudio handles the sound?

---

### Post by Monk-e on 2007-03-25
The Doom 3 engine has problems with ALSA audio (atleast over here anyway). For me it only works when I set it to OSS and speakers to stereo. For this to work you need the alsa-oss package.

---

### Post by MaX on 2007-03-25
Duuh... I had it set to OSS but since pulseaudio took over I've gotten no sound anyway.
Now Doom3 crashes when I try to start it so I can't change back to OSS from ALSA

---

### Post by Monk-e on 2007-03-25
Edit the config file by hand. It should be ~/.doom3/base/DoomConfig.cfg. I'm not sure. Look for s_driver and set it back to "alsa" (no quotes). I'm not sure if Doom3 even works with pulseaudio though...

---


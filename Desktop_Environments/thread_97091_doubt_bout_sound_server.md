---
title: "doubt bout sound server"
date: 2005-11-30
forum: Desktop Environments
---

### Post by sudharshan on 2005-11-30
hi.
now in ubuntu. if i enable the sound server i m not able to get sound from games and other apps...and if i disable it i m unable to hear those system sounds but can hear sounds from apps...how do i enable both sounds at the same time as in other distros

---

### Post by phanboy_iv on 2005-11-30
Hum. Actually I have the same problem. Haven't found a fix that works yet, though.

---

### Post by sudharshan on 2005-11-30
ok heres waht i found out
the trouble i mentioned was with alsa..esd server doesnt hav this problem. the system sounds automatically got shut down while playing games (pingus :))

now i dont know wahts the diff between alsa and esd and my friends recommend alsa over esd...wassup

---

### Post by phanboy_iv on 2005-11-30
I just found a fix that worked for me. 
Frozen Bubble always had no sound if I enabled system sounds. I tried numerous  
fixes. Finally found a fix that works for me on this thread: [http://www.ubuntuforums.org/showthread.php?]("http://www.ubuntuforums.org/showthread.php?t=76872&highlight=Fix+sound+breezy")
Maybe installing libsdl-alsa would fix your problem too?

---

### Post by Zodiac on 2005-11-30
I wonder if this is what happening for me, and why I cannot get sound to work in Enemy Territory...

Are you using ALSA or ESD? (Not that I really know the difference!!)

---


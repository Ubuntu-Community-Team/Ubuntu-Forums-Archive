---
title: "Totem/Mplayer/VLC Vid/Audio Problems"
date: 2005-06-22
forum: Desktop Environments
---

### Post by WAM on 2005-06-22
All of these except VLC can play an all audio .ogg, .mp3, .aac, etc, but for some reason VLC can't. For that matter, Flash doesn't give me any audio either.

None of these can play a .ogg dual audio file w/subtitles correctly. Totem and Mplayer get the audio, but not the video. VLC can get the video and subs, but not the audio. For that matter, VLC can't get audio from a CD or anything either. I've installed all the codecs and things as detailed at the Unofficial Ubuntu Guide. I've tried it with all of the video players. On the other hand, VLC plays it perfectly on the same computer on WinXP.

Thanks.

---

### Post by WAM on 2005-06-22
Anyone?

---

### Post by rachii on 2005-06-22
try this```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

---

### Post by WAM on 2005-06-23
Oh my god. Dude. You're just like 10 minutes late. After about 2 hours of searching threads on the forums etc. I finally found that command and it WORKED!!

Flash and VLC have Audio now!

Thank you for the wonderful advice anyways, I can see you know what you're talking about.  :) 

```
ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.l
```

Magic.

---

### Post by rachii on 2005-06-23
i had the same problem when i first installed, sorry i missed ya, but glad you got it fixed

---


---
title: "Sound Works, then it doesn't"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Koori23 on 2006-07-08
Hi,

I use Streamer XMMS A lot and noticed my sound works most of the time, but not all the time. Is there a way to restart the sound service?. I tend to think that's the issue. I booted into XP and sound worked great, so I'm leaning more toward a software issue than a sound card issue.. Thanks.

---

### Post by mogelhead on 2006-07-10
To restart the sound service, use: 
```
sudo /etc/init.d/alsa-utils restart
```

There is a [trouble shooting guide for sound problems]("https://help.ubuntu.com/community/DebuggingSoundProblems") on the Ubuntu Wiki.

---


---
title: "Totem audio sync problem"
date: 2005-07-05
forum: Desktop Environments
---

### Post by Stilgar on 2005-07-05
Ok, for some reason the sound gets out of sync with the video in totem after a while. At first its hrdly noticeable, but after about 4 or 5 minutes I notice people's lips are out of sync with their words. If I let it play for about 30 minutes ore so the sound is off by about 5 or 6 seconds.

I can hear the sound before I see the video, so either the video is playing slightly too slow or the sound is playing too fast.

If I pause and unpause it syncs back up again (but slowly gets worse as before). So I can watch a video by pausing and unpausing every five minutes, but as you can understand that gets ols pretty fast.

This happens with DVDs and all the various movies saved on my hard disc (divx, xvid, quicktime, etc).

My video card is an ati radeon 9000 (problem occurs under the fglrx driver and the open source "ati" driver). Sound card is and onboard AC'97 SiS (uses the snd_intel8x0 driver). I'm using the 2.6.10-5-k7 kernel.

anyone have any ideas on how I can fix this? It's getting pretty annoying.

---

### Post by Omnios on 2005-07-05
The cure all is to uninstall Totem gstreamer and install totem Xine. I had numerous problems with gstreamer and going Xine fixed them all (choopy and fragged video). 
I think the codec's are set up the same way as in the Unoficial Ubuntu Starters guid + added essential codecs from Mplayer web site and threw them in the codec file (I own producs with official codecs) and now totem rocks.

---

### Post by Stilgar on 2005-07-05
Sorry forgot to mention that I am using totem-xine already. Also gxine shows the same problem. I don't know about totem-gstreamer, since the audio never really worked on that. mplayer is no go since it's got all kinds of crazy dependencies.

Everything is to the most up to date version.

---

### Post by Stilgar on 2005-07-07
Ok I think I got it fixed now. In case someone else has this problem, I'll put what II did here.

I edited /etc/esound/esd.conf so it looked like this:

```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

That seems to have fixed it.

---


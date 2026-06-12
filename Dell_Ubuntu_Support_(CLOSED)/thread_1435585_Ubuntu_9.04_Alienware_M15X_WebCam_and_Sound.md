---
title: "Ubuntu 9.04 Alienware M15X WebCam and Sound"
date: 2010-03-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tstrike on 2010-03-21
For record:

Jaunty Jacklope on Alienware works with the WebCam and Alsa should be modified so that both speaks and headphone jack works with the following steps:

1. Update your alsa level to the latest.
2.  ok now update the config:
```
sudo vi /etc/modprobe.d/50-sound.conf
```50-sound.conf
```

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
# options snd-hda-intel model=3stack-6ch
**options snd-hda-intel model=lenovo-101e**

``````
sudo alsa force-reload
```3. Reboot if necessary.

I have this working with Skype 2.1.x.  :popcorn:

---


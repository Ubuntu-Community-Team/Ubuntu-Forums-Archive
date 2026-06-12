---
title: "Adding multiple Loopback Alsa devices"
date: 2013-08-19
forum: Desktop Environments
---

### Post by am6465 on 2013-08-19
[COLOR=#000000][FONT=Arial]I need to create virtual loopback alsa sinks in my ubuntu setup. I can create one by adding the following to /etc/modprobe.d/sound.conf[/FONT][/COLOR]
```

alias snd-card-0 snd-aloop
options snd-aloop index=21 pcm_substreams=8

```
[COLOR=#000000][FONT=Arial]
I need to create multiple of these but I can't seem to find documentation on how to distinguish between the virtual cards. I would like to create 20.

(Also posted to stackoverflow: [/FONT][/COLOR][http://stackoverflow.com/questions/18321094/adding-multiple-loopback-alsa-devices-in-ubuntu](http://stackoverflow.com/questions/18321094/adding-multiple-loopback-alsa-devices-in-ubuntu))

---

### Post by am6465 on 2013-08-20
Answered from Stack Overflow:
This adds 5 cards when added to sound.conf:
options snd-aloop enable=1,1,1,1,1 index=10,11,12,13,14

---


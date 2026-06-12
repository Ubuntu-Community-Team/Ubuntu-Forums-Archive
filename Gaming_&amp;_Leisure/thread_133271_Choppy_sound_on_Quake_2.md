---
title: "Choppy sound on Quake 2"
date: 2006-02-19
forum: Gaming &amp; Leisure
---

### Post by shade11 on 2006-02-19
I have downloaded and installed Quake 2 and a few maps as well. It works fine with the graphics and everything, except the sound. Can someone please tell me how to fix this sound problem?

---

### Post by porcho on 2006-02-24
I installed both quake2 and quake2-data packages via apt-get, and I was having the same problem here. I've managed to fix it by changing the sound driver used by the game.
By default, quake2 will use the oss sound driver. I've set it up to use libao (with default driver set to ALSA) instead.

To do so, you need to change libao configuration file. Edit /etc/libao.conf changing this line:

```
default_driver=esd
```

to this

```
default_driver=alsa
```

Then, start Quake II using:

```
quake2  +set snddriver ao 
```

I hope it'll work there! :-)

PS: it looks strange to me that I had to use ALSA "through" libao, in spite of using ALSA directly. Fact is, when I tried to do so ALSA would go "buffer underrun" and I got no sound. Anyone knows why that happens?

---


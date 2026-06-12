---
title: "Getting sound to work in games"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by bazar on 2007-03-27
I am using Ubuntu 6.10.  When I install games through Synaptic
(Nexuiz, Tremulous) the audio works perfectly for sound and music
but if try to run any Linux game demos I download from the web
(Quake2, Sin, Doom) there is no audio at all.
Are the SDL/ALSA libraries I obtained through Synaptic no good for
this purpose?  How can I get any audio working for these games I 
download?

---

### Post by lakersforce on 2007-04-23
you might want to try the alsa-oss package. It worked for me.

```
sudo apt-get install alsa-oss
```
and then run the game with, in this case Doom3:
```
aoss ./doom3 
```

---


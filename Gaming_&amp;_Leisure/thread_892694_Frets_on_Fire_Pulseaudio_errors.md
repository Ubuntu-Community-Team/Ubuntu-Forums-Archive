---
title: "Frets on Fire: Pulseaudio errors"
date: 2008-08-17
forum: Gaming &amp; Leisure
---

### Post by janne_oksanen on 2008-08-17
```
janne@Dominator:~$ fretsonfire 
*** PULSEAUDIO: Unable to connect: Connection refused
*** PULSEAUDIO: Unable to connect: Connection refused
*** PULSEAUDIO: Unable to connect: Connection refused
*** PULSEAUDIO: Unable to connect: Connection refused
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device
janne@Dominator:~$ 

```

Any ideas?

---

### Post by Mr. Bunny on 2008-08-18
I have a similar problem:

```
$ ./FretsOnFire
ALSA lib ../../../src/pcm/pcm.c:6625:(snd_pcm_slave_conf) unknown format unchanged
ALSA lib ../../../src/pcm/pcm.c:6625:(snd_pcm_slave_conf) unknown format unchanged
ALSA lib ../../../src/pcm/pcm.c:6625:(snd_pcm_slave_conf) unknown format unchanged
ALSA lib ../../../src/pcm/pcm.c:6625:(snd_pcm_slave_conf) unknown format unchanged
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 68, in ?
  File "src/GameEngine.py", line 149, in __init__
  File "src/Audio.py", line 49, in open
pygame.error: No available audio device

```

I get the same results when running with pasuspender ./FretsOnFire

I'm running Frets on Fire v 1.2.512.

---

### Post by Orlsend on 2008-08-19
Is this with the Repo one or the site script one?

---

### Post by Yellow Onion on 2008-10-06
this is slightly off topic, how do I change it to alsa instead of using pulse audio?

---

### Post by doorknob60 on 2008-10-08
System > Preferences > Sound > Change everything from Pulseaudio to ALSA.

---


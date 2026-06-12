---
title: "Frets On Fire,  No available audio device"
date: 2008-08-26
forum: Gaming &amp; Leisure
---

### Post by peepymouse on 2008-08-26
Im using Linux , ubuntu and i keep getting the message 
```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 64, in ?
  File "src/GameEngine.py", line 149, in __init__
  File "src/Audio.py", line 49, in open
pygame.error: No available audio device

```
im using ubuntu Hardy Heron and i use OSS sound system/driver please help me

---

### Post by Orlsend on 2008-08-26
Is this from the Repo or the script from the Site?

---

### Post by peepymouse on 2008-08-26
> **Orlsend said:**
> Is this from the Repo or the script from the Site?

Repo ??? i dint used the script from the site

i just downloaded the .tar.gz and untar'ed it 
download source : SourgeForge.net.

---

### Post by _sphinx_ on 2008-09-28
I am experiencing exactly the same problem except I am using alsa drivers. Please help me in this regards..

---

### Post by NoThanksM$ on 2008-11-29
I'm also having this problem, using x86 version of Intrepid 8.10.  I set up a new action in Sessions so that each time I log in, the pulseaudio process is killed because it was causing more problems than it was worth and I was advised that uninstalling it is not a good idea.  However, now I get the same error you're getting unless I start the PulseAudio process first.

---


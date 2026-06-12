---
title: "ZSNES sound issues"
date: 2010-08-13
forum: Gaming &amp; Leisure
---

### Post by Majin Zero on 2010-08-13
Ubuntu 10.04 32 bit

I grabbed ZSNES 1.51 via synaptic, but I'm having nothing but sound issues with it.

Using pulse audio, I'll have constant cracking and popping

using ASLA or ESD, there will be no popping, however the audio will be so delayed the game is unplayable

using OSS - there is no sound what-so-ever

Any ideas on how to correct this?

---

### Post by djinnkeeper on 2010-08-13
I remember having this problem, but I don't remember doing anything other that getting rid of Pulse and switching to ALSA, as you've just said didn't entirely work.  Not sure what to make of that, or if I'm forgetting part of my own past woes.

At any rate, I just overcame a crackling/popping problem (this time in 64-bit Ubuntu, but with dfreer's 32-bit ZSNES repack).. again, I'm not entirely sure what did it, or even if the problem is related to the crackling I experienced in 32-bit Ubuntu, but the last thing I changed was switching to 32000hz quality.  Also, I am not using any interpolation or lowpass filter.  Dunno if that is affecting it.

Sorry I'm not much help and you've probably already tried futzing with the sound configuration in ZSNES.  At any rate, bumped the thread.  :D

---

### Post by Majin Zero on 2010-08-14
Yes, sadly, I've tried every sound configuration I can think of both with the popping/cracking sound mixers and the "delayed" ones.

Nothing seems to remedy either issue.

---

### Post by frenchn00b on 2010-08-15
> **Majin Zero said:**
> Yes, sadly, I've tried every sound configuration I can think of both with the popping/cracking sound mixers and the "delayed" ones.

Nothing seems to remedy either issue.

it is a bit strange because zsnes is buggyless

I would you use surely alsa, and maybe work hard on
alsamixer -e 
even try to reboot once
try to stick to default config files
...

certanly you tried everythig

what does say : 
```
 cat /proc/asound/cards
```

---

### Post by dfreer on 2010-08-15
> **frenchn00b said:**
> it is a bit strange because zsnes is buggyless

0_o It totally just isn't. See the 17 pages in my thread alone if not convinced.

EDIT: Well, technically most of the problems are actually with Ubuntu/pulseaudio/linux/libao/whatever, but zsnes is definitely not free of bugs. As for scratchiness of sound in ZSNES, here's a thread I created regarding sound quality and some tests I did. Of course, with newer versions of Ubuntu released and differences in other users hardware, this may not actually be helpful.
[http://ubuntuforums.org/showthread.php?t=851396](http://ubuntuforums.org/showthread.php?t=851396)

---


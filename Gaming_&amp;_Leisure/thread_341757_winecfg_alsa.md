---
title: "winecfg alsa"
date: 2007-01-19
forum: Gaming &amp; Leisure
---

### Post by MdChaos on 2007-01-19
Hi!

I'm a linux noob, I tried hard but I couldn't solve this problem:

Everytime I go to the  AUDIO-Panel in winecfg, this message is put out:

ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: not found
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

---

### Post by earobinson on 2007-01-24
I to would like the answer to this

---

### Post by EvilMarshmallow on 2007-01-24
BUMP!

I too need an answer to this.  I installed just about every other package related to alsa I could find in the repos, and got nowhere.  I'm thinking it's a sound driver issue but I need a bigger Ubuntu geek than I to help me solve the problem.

---

### Post by earobinson on 2007-01-24
Ya im thinking its a problem with the sound card 2, I rember tweaking with my sound settings when I installed ubuntu not sure what i did though.

---

### Post by Sammi on 2007-01-25
What soundcard are you guys using?

---

### Post by EvilMarshmallow on 2007-01-25
Mine is onboard with my motherboard.  I researched it a little bit to find that it was an "Analog Devices AD1885" Chipset.

Sounds work for me, good quality and everything, they just lag when I run Call of Duty via Wine.  System sounds are lag-free.  I tried native OpenGL-type apps such as SuperTux, and sounds are fine there too.

I get a DSOUND underrun error a lot when running Call of Duty as well, but the only other errors I can find seem to be the one listed by the OP.

---

### Post by earobinson on 2007-01-25
I will check when I get home but mine is also on board

---

### Post by Jarn on 2007-01-25
To prevent the /dev/snd/seq error, do:
```
sudo modprobe snd-seq-oss
```

---

### Post by EvilMarshmallow on 2007-01-25
ok, that cuts down on the error messages in the terminal...

I still have a delay problem with sounds in Wine.  All sounds are correct, good quality, but they lag behind the video by about half a second... really distracting in Call of Duty.

Any ideas?

---


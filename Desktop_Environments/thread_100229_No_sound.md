---
title: "No sound"
date: 2005-12-07
forum: Desktop Environments
---

### Post by micder on 2005-12-07
There is something wrong with the detection of my soundcard:
a SoundBlasterLive 24bit.

In other distros it's recognized as ca0106 and plays well.

lspci gives: 0000:01:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
That's OK

lsmod |grep -e snd gives:
snd_ca0106             27172  0
snd_ac97_codec         72188  1 snd_ca0106
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  5 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_ca0106,snd_hda_intel,snd_pcm

Sustem > Preferences > Sound gives me a choice of HDA Intel (default) or ca0106.
Changing from default to ca0106 has no success.

Alsamixer shows:
Card: HDA Intel
Chip: Realtek ALC880 ?????

I tried to select the right card with alsaconf, but the command is unknow.

Any help or hint is much appreciated

---

### Post by micder on 2005-12-08
Problem solved :) 
Had to disable onboard sound card.
Did not know I had one :-o 
Windhose and other distros did not detect this card.
Ubuntu hardware detection is super

---


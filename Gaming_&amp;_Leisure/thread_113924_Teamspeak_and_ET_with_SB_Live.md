---
title: "Teamspeak and ET with SB Live"
date: 2006-01-07
forum: Gaming &amp; Leisure
---

### Post by patwest on 2006-01-07
I just found an old SB Live cheap so I replaced my motherboard sound with it expecting it to fix the problems because it has HW mixing.

I still need to use:
```
#!/bin/sh
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

lspci sees it as the EMU10K1 based SB Live card
```
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
```

I read people saying that they didn't have to do anything to get this setup to work. I might have tried changing some files in order to get it to work with the on board sound. Should I still need to run these commands or is something setup incorrectly?

Patrick

```
$ lsmod | grep emu10k1
emu10k1_gp              3712  0 
gameport               14920  2 emu10k1_gp
snd_emu10k1_synth       7616  0 
snd_emux_synth         36096  1 snd_emu10k1_synth
snd_emu10k1           118404  3 snd_emu10k1_synth
snd_rawmidi            25056  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8524  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         84028  1 snd_emu10k1
snd_pcm                89032  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10696  2 snd_emu10k1,snd_pcm
snd_util_mem            4544  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8992  2 snd_emux_synth,snd_emu10k1
snd                    55172  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep

```

---

### Post by hav0x on 2006-01-07
What is the problem?

---

### Post by patwest on 2006-01-07
[QUOTE=hav0x]What is the problem?[/QUOTE]
I thought I had read somewhere that you didn't need to run those commands when you had a card with HW mixing, like the SB Live.

Patrick

---


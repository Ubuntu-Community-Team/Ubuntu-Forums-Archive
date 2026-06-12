---
title: "SB Live! EMU10K1 issues"
date: 2006-01-17
forum: General Help
---

### Post by Ryan450 on 2006-01-17
hey gang,

since the initial install of my ubuntu desktop install, I've been having a hard time getting my sound to work.. first thing I did was jump onto the IRC channel, drac-laptop was trying to help me out.. I'll attach the chat log to a file for viewing as well.

the card is a SB Live! EMU10K1 according to my device manager... heres some of the things we've tried and still have no luck with.. 

```

root@fletchbox-ubuntu:~# lsmod | grep snd
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  1 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
 snd_ac97_codec         72188  1 snd_emu10k1
 snd_pcm_oss            46368  0
 snd_mixer_oss          16128  1 snd_pcm_oss
 snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
 snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
 snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
 snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
 snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
 snd                    48644  13 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
 soundcore               9184  1 snd

root@fletchbox-ubuntu:~# modprobe snd-emu10k1
root@fletchbox-ubuntu:~# lsmod | grep snd
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  1 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  13 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
root@fletchbox-ubuntu:~# exit
exit
ryan@fletchbox-ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
ryan@fletchbox-ubuntu:~$

```

thats the information that I still have avaliable from the issue, sadly I've lost most of the log file, so it will be pointless to attach it now.. (damn chat history buffer).. any suggestions/thoughts on the issue?

---


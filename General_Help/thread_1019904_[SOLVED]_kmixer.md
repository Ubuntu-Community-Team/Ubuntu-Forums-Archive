---
title: "[SOLVED] kmixer?"
date: 2008-12-23
forum: General Help
---

### Post by firsttimeuser on 2008-12-23
just upgraded from 8.04 to 8.10 and got no sound, I noticed there is no speaker icon on the system panel. I remember there should be a kmixer there. 

So what is the command to bring up the kmixer? I want to check if the mute option is on.

---

### Post by oilchangeguy on 2008-12-23
> **firsttimeuser said:**
> just upgraded from 8.04 to 8.10 and got no sound, I noticed there is no speaker icon on the system panel. I remember there should be a kmixer there. 

So what is the command to bring up the kmixer? I want to check if the mute option is on.

no speaker icon=kubuntu does not see any sound card.

---

### Post by firsttimeuser on 2008-12-23
but it seems the system sees my hardware, as below...

laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.17.
laptop:~$ cat /proc/asound/cards
0 [I82801DBICH4 ]: ICH4 - Intel 82801DB-ICH4
Intel 82801DB-ICH4 with AD1981B at irq 11
laptop:~$ lsmod | grep snd
snd_intel8x0 37532 0
snd_ac97_codec 111652 1 snd_intel8x0
ac97_bus 9856 1 snd_ac97_codec
snd_pcm_oss 46848 0
snd_mixer_oss 22784 1 snd_pcm_oss
snd_pcm 83204 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 10884 0
snd_seq_oss 38528 0
snd_seq_midi 14336 0
snd_rawmidi 29824 1 snd_seq_midi
snd_seq_midi_event 15232 2 snd_seq_oss,snd_seq_midi
snd_seq 57776 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 29960 2 snd_pcm,snd_seq
snd_seq_device 15116 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 63268 10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
soundcore 15328 1 snd
snd_page_alloc 16136 2 snd_intel8x0,snd_pcm

---

### Post by todak on 2008-12-23
Right-click on the desktop and choose Run application.. and in the entry bar that appears type in the command **kmix**

---

### Post by SuperSonic4 on 2008-12-23
+1 for kmix

---

### Post by firsttimeuser on 2008-12-23
ah, thanks a lot!

After I disabled the mute option, I got sound! 

> **todak said:**
> Right-click on the desktop and choose Run application.. and in the entry bar that appears type in the command **kmix**

---


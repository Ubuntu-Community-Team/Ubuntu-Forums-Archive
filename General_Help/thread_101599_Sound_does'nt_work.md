---
title: "Sound does'nt work"
date: 2005-12-10
forum: General Help
---

### Post by Evisu on 2005-12-10
Hi, 
hi have an on-board sound card with the SIS 7012 chipset and i cant get sound to work in ubunt.
here's the output of some commands: 
root@roby:~# lsmod | grep snd
snd_mpu401              6344  0
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

aplay commands works fine, it doesnt give errors but i simply dont hears sound.
i've already checked the volumes in the mixers and they're all ok.
thank you for any help

---

### Post by N0Ga on 2008-02-17
may i ask .... i have setuped ubuntu 
and when i make it works no sound my laptop is 530 hp 
and what are these commands???
i can not no what are these???

---


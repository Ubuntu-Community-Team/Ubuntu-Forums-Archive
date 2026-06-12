---
title: "Slight upgrade issue"
date: 2005-12-13
forum: General Help
---

### Post by elminster13 on 2005-12-13
I have recently upgraded my system from hoary to breezy and I must confess even though I use a lot of disperate applications it handled it well. Well done to the development team.

One problem i did find after upgrade was I had no sound, as my /dev/dsp or esd was missing. I read through the forums and found a fix by moving all my applications over to alsa which works well until I get to vmware.

Vmware doesn' thave support for alsa and as such I need to use esd, or at list have /dev/dsp linked to a mixer of some sort. Does anyone have any suggestions?

Heres some system info:
lspci | grep audio
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller

lsmod | grep snd
snd_via82xx            25792  1
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm                78344  2 snd_via82xx,snd_ac97_codec
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  9 snd_via82xx,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd

In all other activities sound is fine I followex this tread to get things working with alsa: [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

---


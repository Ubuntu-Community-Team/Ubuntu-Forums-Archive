---
title: "Just another sound problem"
date: 2005-12-18
forum: General Help
---

### Post by delm on 2005-12-18
Here it is:
I installed breezy like 4 weeks ago, and it worked "Just Fine". Sound included.
But suddently it stopped working. I tried fixes from here in all topics and in other pages on the web but at not avail.
The weird is that sometimes when i play with alsamixer i get sound, but just for some time (for a song or until i close bmp or gxine or whatever).
I have a VIA 8237 and i tried to mute IEC958 capturer, but when i play some sound (anything) it auto enables itsef. O_o
here is the technical stuff
```
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
$ lsmod | grep snd
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  15 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
```
```
$ lspci | grep Multimedia
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

i have modified so many config files that i dont know wish one post here.

My guess is that some update caused this sound failure... but im kindda inexperienced in linux.

help please, i love ubuntu, but this sound "issue" just sox

---

### Post by delm on 2005-12-21
help please!!

---


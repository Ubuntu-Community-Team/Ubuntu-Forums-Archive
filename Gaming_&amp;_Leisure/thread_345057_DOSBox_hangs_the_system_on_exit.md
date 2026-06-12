---
title: "DOSBox hangs the system on exit"
date: 2007-01-23
forum: Gaming &amp; Leisure
---

### Post by Number6 on 2007-01-23
Hi everyone, I was just trying out DOSBox and kept getting the following error:

```
ALSA lib seq_hw.c:456: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer

```
so I tried a : 

```
sudo modprobe snd-seq
```

which worked and then DOSBox was happy until i tried to quit! Then the entire system hangs and I have to reboot! 

HELP! I wanna play some DOS games!! :confused: ](*,)

---

### Post by Stemp on 2007-01-23
When i start dosbox i have a similar message :

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none
```

But no problems when quitting, I guess your problem is not related to sound.

---


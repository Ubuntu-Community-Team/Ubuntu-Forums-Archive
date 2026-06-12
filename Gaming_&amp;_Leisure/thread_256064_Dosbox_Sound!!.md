---
title: "Dosbox Sound!!"
date: 2006-09-12
forum: Gaming &amp; Leisure
---

### Post by jimmyxx on 2006-09-12
Hi all,
Just descovered dosbox - I love it! i so missed theme hospital!

Want to get sound working though, when i launch dosbox this comes up:

jimmy@jimmypad:~$ dosbox dos
CONFIG: Using default settings. Create a configfile to change them
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none

The game works fine, just really miss the sound of the rats splat as i shoot them with my minigun!

Any help would be great, thanks!

---

### Post by gborzi on 2006-09-12
You need to enable Software midi, look here [https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo) and also to copy the example configuration file /usr/share/doc/dosbox/dosbox.conf.example.gz to ~/.dosboxrc (obviously, gunzip it), open it with your preferred text editor and change the config option under the "midi" section from config= to config=128:0. In general it is helpful to put > export ALSA_OUTPUT_PORTS="128:0" at the end of your ~/.bashrc file.

---


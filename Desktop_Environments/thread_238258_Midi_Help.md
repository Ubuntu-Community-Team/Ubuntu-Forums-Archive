---
title: "Midi Help"
date: 2006-08-17
forum: Desktop Environments
---

### Post by shagey36 on 2006-08-17
Hi ive been trying to get the program Kguitar to work but i didnt have a midi device...so i installed timidity as a midi sequencer and now when i run kguitar i see

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kguitar: MIDI Scheduler created

and no sound plays when i try to play a song.....anybody have any ideas?

---

### Post by Cryonic on 2006-08-17
Not a direct solution to your problem, but I had more luck with Tuxguitar. It's in the Universe/Multiverse repositories. Make sure you install with synaptic or in a terminal with "sudo aptitude install tuxguitar" because it has some dependencies. Like KGuitar, it has support for gp3 through gp5.

---


---
title: "Kguitar - no sound"
date: 2006-01-21
forum: Desktop Environments
---

### Post by lrmall01 on 2006-01-21
Anybody here use kguitar?  I searched and didn't find any threads, so maybe not.

I can't get any sound out of it.  Whenever I try going to the settings menu to see if I have to tell it to use Timidity the program crashes.

---

### Post by FarEast on 2006-01-23
It is an interesting apprication!
(I know next to nothing about it, though.)

> Whenever I try going to the settings menu to see if I have to tell it
> to use Timidity the program crashes.

Does it use ALSA MIDI interface for playing music?
If so, execute 'aconnect -o' to see available ports.

---

### Post by lrmall01 on 2006-01-24
Looks like nothing is connected.

client 62: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'

---

### Post by FarEast on 2006-01-24
I installed kguitar and tried 'Settings > Configure KGuitar'.
It crashed!!  I am sorry, but I do not know what to do for the moment :(.

-----
PS
I compiled it from source and result was the same.
It seems that other guys also have the problem.
[http://sourceforge.net/forum/forum.php?thread_id=1374827&forum_id=24021](http://sourceforge.net/forum/forum.php?thread_id=1374827&forum_id=24021)

---

### Post by calsaverini on 2006-12-16
I've installed Kguitar and it works well apart from not playing midi.

When I go to the configuration menu no midi device appears in the list. I don't know how to tell the progam to use timidity.

---

### Post by calsaverini on 2006-12-16
When I run kguitar I get the following error message in the terminal:

[B]
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ALSA lib seq_hw.c:457: (snd_seq_hw_open) open /dev/snd/seq failed: Arquivo ou diretório inexistente
TSE3: Alsa scheduler error. Couldn't open sequencer
      (Arquivo ou diretório inexistente)
[/B]

The program does not crash but it does not play the notes. 
No midi device appear in the list in the configuration menu.

---

### Post by gabo on 2007-05-28
Well my Kguitar works well but no sound.
I am using timidity for virtually generating midi ports

I can play midi with other programs but eventhough my KGuitar configuration shows the timidity ports it still doesn't work

Man...

---


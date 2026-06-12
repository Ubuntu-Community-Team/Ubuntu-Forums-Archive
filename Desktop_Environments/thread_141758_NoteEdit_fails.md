---
title: "NoteEdit fails"
date: 2006-03-09
forum: Desktop Environments
---

### Post by tophat2445 on 2006-03-09
ok, I installed noteedit from synaptic but when I try to run it, all I get is a short splash screen.  I tried to run it from the terminal, and this is what I got: 

kenny@HOME2:~$ noteedit
kbuildsycoca running...
LilyPond check: found version: 2.6.3
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
TSE3: Alsa scheduler error. Couldn't open sequencer
      (No such file or directory)
terminate called after throwing an instance of 'TSE3::MidiSchedulerError'
  what():  Failed to create the MIDI scheduler
KCrash: Application 'noteedit' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
kenny@HOME2:~$


-Please help

Kenny

---

### Post by dcstar on 2006-03-09
[QUOTE=tophat2445]ok, I installed noteedit from synaptic but when I try to run it, all I get is a short splash screen.  I tried to run it from the terminal, and this is what I got: 
.......[/QUOTE]
Noteedit "suggests" the following other packages be installed (apart from the other dependencies, which I assume you have installed):

timidity, then lilypond OR musixtex OR abcm2ps OR pmx.

I suggest you install the first one as well as one of the others.

---


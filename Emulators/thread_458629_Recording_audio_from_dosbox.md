---
title: "Recording audio from dosbox"
date: 2007-05-29
forum: Emulators
---

### Post by georgecm3 on 2007-05-29
Is there a way I could record the music from a game that is being played in dosbox?

---

### Post by BoyOfDestiny on 2007-05-29
> **georgecm3 said:**
> Is there a way I could record the music from a game that is being played in dosbox?

Yes,

From the dosbox readme (type man dosbox)

       CTRL-F6     Start/Stop recording sound output to a wave file.

       CTRL-ALT-F7 Start/Stop recording of OPL commands.

       CTRL-ALT-F8 Start/Stop the recording of raw MIDI commands.

Make sure to define a location for the captures to go to (here is mine in my dosbox.conf)

[I][dosbox]
# language -- Select another language file.
# memsize -- Amount of memory dosbox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,pcjr,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=vga
**captures=/home/yourusername/whateverfolder**
memsize=16[/I]

It will store screencaps, audio rips etc there.

---

### Post by spotsnz on 2012-01-06
How do I edit this dosbox.conf?

I went to places>search for files, and searched for dosbox.conf and it didn't find it (it returned immediately though, doesn't seem like it looked for it).

solved:

$ cd ~/.dosbox/

---

### Post by Perfect Storm on 2012-01-07
Necromancing, thread closed.

---


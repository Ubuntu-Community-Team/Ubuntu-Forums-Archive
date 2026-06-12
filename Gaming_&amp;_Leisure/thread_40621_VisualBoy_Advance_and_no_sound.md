---
title: "VisualBoy Advance and no sound"
date: 2005-06-09
forum: Gaming &amp; Leisure
---

### Post by Holonomci on 2005-06-09
I just installed Ubuntu 5.04 on my Dell Inspiron 6000.  The sound kind of works, in that Gnome can play sounds for events.  Unfortunately, whenever I try to start up VBA, it tells me "Failed to open audio: No available audio device".  Of course, it still runs, but without the sound, VBA simply runs at full speed.  Anyone know what is going on?  

Oh, as an aside, sound is also broken in any media player (XMMS, VLC, Totem).

---

### Post by rogeriovinhal on 2005-08-05
I also have no sound.
Tried that sound configuration shown in ubuntuguide, but all that did was preventing my gnome of starting.

I also can't figure out how to make the games work in 100%. Everytime they are like 300%, or 200%.

When I run vba, it shows this:

```
Failed to open audio: No available audio device
```

---

### Post by Seth on 2005-08-05
[QUOTE=rogeriovinhal]I also have no sound.
Tried that sound configuration shown in ubuntuguide, but all that did was preventing my gnome of starting.

I also can't figure out how to make the games work in 100%. Everytime they are like 300%, or 200%.

When I run vba, it shows this:

```
Failed to open audio: No available audio device
```[/QUOTE]
 You have to killall esd before starting vba.

---

### Post by rogeriovinhal on 2005-08-05
Actually i managed to make sound work just re-doing the configuration from Ubuntuguide, and this time it didn't crash my gnome... I reaaly don't understand why and really don't care that i don't understand, because it works right now.  :) 

And the percentage now is fixed on about 99%, so it was a sound problem after all. ^^

---


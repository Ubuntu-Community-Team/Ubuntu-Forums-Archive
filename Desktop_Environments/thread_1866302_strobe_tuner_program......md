---
title: "strobe tuner program....."
date: 2011-10-21
forum: Desktop Environments
---

### Post by boblizar on 2011-10-21
lingot, gxtune, rakarrack, and fmit are all guitar tuners, but none of them work as a strobe tuner, and in general they are all buggy and jumpy tuners....  can someone write a program that acts as a strobe tuner, that takes wave forums and compresses them into square waves that takes a sampling and in general compares it to a known tonal pitch?

lingots the best out of all of them, and it doesnt know an A from a D!!!!  it registers harmonics and jumps all over the place instead of seeing raw data of 220 up phases and registers harmonics 220, 440, 880 instead of seeing the original 220 and nothing else.  theres a problem with this as the perfect fifths create meshing harmonic tones and the program registers the over tone and perfect fifth as the tone that is being tuned.  long story short all the guitar tuners = F quality, and a tone generator on audacious is a far more viable solution.

problem with tone generation is that many musicians are tone deaf.  heres a video of a strobe tuner so you get the idea of what im looking for...  i picked a video where the guy has hawk hair for your entertainment :lolflag:

[http://www.youtube.com/watch?v=JmgoI3Z0Plw](http://www.youtube.com/watch?v=JmgoI3Z0Plw)

---

### Post by Frogs Hair on 2011-10-21
I don't know if this is any better than the programs you have written about . I have a tuner , but don't use one on my computer . [http://sourceforge.net/projects/lstune/](http://sourceforge.net/projects/lstune/)

---

### Post by boblizar on 2011-10-21
./lstune: error while loading shared libraries: libQtMultimedia.so.4: cannot open shared object file: No such file or directory

lstune might be better if it wasnt broken, and the threads marked for ubuntu, most people dont want to install KDE libraries.  i actually have KDE libraries on here, but i cant find libqtmultimedia or compile it.

long story short, working in the first place is required :D  id prefer a GTK+ version of lstune if possible that would work on the standard ubuntu distribution with out hoops to jump through

[http://code.google.com/p/ctuner/](http://code.google.com/p/ctuner/) is windows / mac only

gtkguitune = no /dev/dsp for ubuntu  how do i get /dev/dsp back?

---


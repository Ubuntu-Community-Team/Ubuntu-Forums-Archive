---
title: "FCEU very slow"
date: 2009-05-26
forum: Gaming &amp; Leisure
---

### Post by docjones2 on 2009-05-26
I'm trying to play Ninja Gaiden on my Linux!  I'm running Ubuntu 9.04, I have a 3 GHz Pentium 4 with 1 Gb of RAM, I doubt it's low system specs that are causing my troubles.

FCEU plays at a VERY low frame rate, close to 5 times slower than real time.  Logic told me that using OpenGL would increase the speed, OpenGL actually made it twice as bad (somehow), I'm also using the lowest allowed number of bits per pixel, 8.  Audio is disabled.

There are no proprietary video drivers in use on my system, and to the best of my knowledge none are available.

Any ideas?

---

### Post by BoyOfDestiny on 2009-05-26
You can try going to System -> Preferences -> Appearance -> Visual Effects
Set Visual Effects to none.

FCEU is out of date as far as I know (there are newer forks...)

You could give [mednafen]("http://mednafen.sourceforge.net/") a go.

sudo apt-get install mednafen

Right click on your rom, choose open with mednafen

Press F1 for help (how to map your controller and so on)

If you want to customize the config further (i.e. simulate ntsc television picture), check your ~/.mednafen folder.

---

### Post by docjones2 on 2009-05-26
Thank you very much!  Later I'll take a look at the various graphics options, but this emulator does run at full speed.

---

### Post by svtguy88 on 2009-05-26
Interesting.  I run FCEU (well, FCEUX) on a similar machine (P4, 2.66ghz, 2gb), and it work reasonably well.  It does bog from time to time (not sure why), but it's almost never an issue.  Try running FCEUX instead.  It's pretty much a merger of FCEU and GFCEU (as far as I understand it), but maybe some portions got updated and it will work better for you?

Just a thought.

---


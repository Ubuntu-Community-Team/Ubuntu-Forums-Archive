---
title: "integrated sound blaster"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by John Hoge on 2007-08-09
I have an old dell that I'm trying to bring back to live with Ubuntu. I did a fresh install from the alernate 7.04 CD but have no sound.

My system has an integrated Sound Blaster card, but Ubuntu doesn't seem to recognize it.

john@ubuntu:~$ cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xdf00, irq 3

---

### Post by ridgeland on 2007-08-10
I've had a few installs that did not have sound but were just a settings problem.  My sound blaster driver defaulted to 'Digital' output cable when I had simple (analog?) speaker connections.  A toggle of the switch solved it.  My wife's laptop also installed with no sound and a toggle switch solved it.  
Maybe you could be so lucky... Try double clicking on the speaker icon and try everything you can find, especially in edit -> preferences.
If no luck there my next stop is to try 
menu -> System -> Preferences -> Sound 
and try everything there, all the driver options, tests etc.

---


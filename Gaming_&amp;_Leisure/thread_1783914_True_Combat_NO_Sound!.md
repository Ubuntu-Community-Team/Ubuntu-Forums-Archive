---
title: "True Combat NO Sound!"
date: 2011-06-16
forum: Gaming &amp; Leisure
---

### Post by Fookenmonkey on 2011-06-16
I download true combat yesterday. But there is no sound and i get this error in the sound initialization in the game

/dev/dsp: No such file or directory
Could not open /dev/dsp

What does that mean?

---

### Post by KindredCharles on 2011-06-17
I have always used this fix for sound on tce.

[http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231)

good luck.

---

### Post by Kodeine on 2011-06-18
I played on CQB a tad. Though it seems there is only one map to play on and a hand full of servers. Is the regular true combat the same?

---

### Post by auxilium on 2013-01-23
Hi,

Same Problem here, no sound for CQB. I tried this link

[http://linuxgamecast.com/2011/04/l-g-c-how-to-%E2%80%94-truecombat-close-quarters-battle-cqb/](http://linuxgamecast.com/2011/04/l-g-c-how-to-%E2%80%94-truecombat-close-quarters-battle-cqb/)

works fine but I can't get my sound working.

i tried to run in the terminal
```
 ./et-sdl-sound 
```
it shows the wrong path where to find the libsdl-sound. i think it should be somewhere in /usr/lib folder.

I am using ubuntu 12.04.1. I had also installed the following files using synaptics

libsdl-sound1.2
libsdl1.2-dev

---


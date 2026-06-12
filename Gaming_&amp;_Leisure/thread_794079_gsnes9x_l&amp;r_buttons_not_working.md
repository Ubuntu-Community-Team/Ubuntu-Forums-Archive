---
title: "gsnes9x l&amp;r buttons not working"
date: 2008-05-14
forum: Gaming &amp; Leisure
---

### Post by yon2501 on 2008-05-14
just noticed this problem now while playing chrono trigger, got to a point in the game where i have to use l and r in conjunction with a and the l and r buttons dont work. unless im mistaken the l and r buttons are a and z correct? now the problem is i see no place to change the keyboard button mapping in the program. any suggestions?

---

### Post by dfreer on 2008-05-14
Dunno about what keys are mapped to L and R in gsnes9x. I know that this is a common problem with chrono trigger, because you can't get the keyboard to accept all three key presses at once.

The workaround in zsnes is to map all three buttons to one key, such as ; or something. 

My suggestion would be to use zsnes instead ;)

---

### Post by yon2501 on 2008-05-14
ok then ill try zsnes but where do i transfer my saves to zsnes or do i have to start over cuz that would suck

---

### Post by dfreer on 2008-05-14
> **yon2501 said:**
> ok then ill try zsnes but where do i transfer my saves to zsnes or do i have to start over cuz that would suck

Save your game using the in game save feature (not save state). This should create a *.srm file either in the directory with all of your roms, or somewhere in your home folder (not entirely sure where gsnes9x saves stuff, maybe ~/.gsnes9x/). 

I think zsnes places it's saved games in ~/.zsnes/
Best thing would be to load a new copy of chrono trigger in zsnes, save a game quickly, figure out where it placed the save, and then copy your old save from gsnes9x to the same location/name as the zsnes save.

ZSNES doesn't play entirely nice with Hardy + Pulseaudio, if you are currently running that btw. ZSNES is probably the best SNES emulator though.

(NOTE: This is all off the top of my head, I may have gotten some of this wrong. Make sure to back up your saved game before you load it in ZSNES, in case something goes wrong.)

---


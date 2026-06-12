---
title: "i can't turn back into ctrl+alt+f8"
date: 2008-01-13
forum: Desktop Environments
---

### Post by kr0n1x on 2008-01-13
Hi, my terminal works good (f1 to f6 and f7 for graphic)

but today i made a script for a game, to launcht that game into a virtual session:
```
#!/bin/bash
xinit /usr/local/games/enemy-territory/et-sdl-sound $* -- :1
```

it works well, i can play, and i can switch to my desktop pressing ctrl+alt+f7 :)

but if i try to come back into the game (pressing ctrl+alt+f8) i get a black screen...with some words... i know these words are from boot... like:

> * Running local boot script blablabla [OK]

and nothing more...

what can i do?

i'm in ubuntu gutsy 7.10 64bit

thanks, bye

---

### Post by kr0n1x on 2008-01-13
lol i had a bit of luck :)

i tried other console while the game was ON.

i found my game (in virtual session) on ctrl+alt+f5

---


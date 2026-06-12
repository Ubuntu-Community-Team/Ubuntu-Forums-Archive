---
title: "XMAME is not recognizing the games."
date: 2006-11-20
forum: Gaming &amp; Leisure
---

### Post by Gotterdammerung on 2006-11-20
I've installed kxmame, xmame and xmess in my system hoping to play some cool old game, but xmame is not recognizing my game files. How can I solve this? Or at least, how can I make myself sure that it is at least verifying them?

Thanks in advance.

---

### Post by leech on 2006-11-20
Oddly enough I just ran into something similar with Gauntlet 1 and 2 within Mythgame.  

Other games were working just fine though.

Leech

---

### Post by NESFreak on 2006-11-21
try running ```
xmame -verifyroms
```
it checks if all the roms are there. (the zip archives aren't the rom files, they contain the rom files, which in most cases are more then one rom file. so if your missing one or two you wont notice(apart from the fact that the game doesn't work)

NESFreak

---

### Post by Gotterdammerung on 2006-11-21
It is not working...

What about the directories? kxmame is looking for them in the wrong path (/usr/lib/games/xmame).

---

### Post by NESFreak on 2006-11-22
can you run the games from the commandline?

---


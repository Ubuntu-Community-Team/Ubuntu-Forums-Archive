---
title: "lost laby crashes"
date: 2008-02-11
forum: Gaming &amp; Leisure
---

### Post by eilu on 2008-02-11
Whenever I quit laby (from the title menu or in-game) the game gets a segmentation fault. These are from the last three:
[INDENT]/usr/bin/laby: line 3:  7955 Segmentation fault      (core dumped) ./laby
/usr/bin/laby: line 3:  8248 Segmentation fault      (core dumped) ./laby
/usr/bin/laby: line 3:  8266 Segmentation fault      (core dumped) ./laby[/INDENT]
This also has the unfortunate consequence that my settings (english language, scroll speed, message speed, etc) and changes (highscore entry, saved games) do not persist from one game session to another.

Also, the same thing happens when I try to access the readme/help from in-game. Again:
[INDENT]/usr/bin/laby: line 3:  8282 Segmentation fault      (core dumped) ./laby[/INDENT]

I am running the game on an Ubuntu Gutsy 7.10; I downloaded the DEB from the site (lostlabyrinth.com) and installed it via GDebi; it's version 2.9.0

I tried changing laby's folder permissions to allow me to read/write (since it is a root folder) but still no dice. Any ideas?

---


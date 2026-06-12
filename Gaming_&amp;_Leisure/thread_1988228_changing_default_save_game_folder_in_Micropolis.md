---
title: "changing default save game folder in Micropolis"
date: 2012-05-27
forum: Gaming &amp; Leisure
---

### Post by Erik1984 on 2012-05-27
Micropolis is an open source version of the original sim city game that is in the Ubuntu repositories :) I like it (especially the mega dry sound effects) but there is one little annoyance: Micropolis tries to save games in /usr/share/game/micropolis/cities. first that folder is owned by root so Micropolis can't actually save games there and second I want any personal application data like save games in my home folder. I can't find an option to change the default save game location. Any ideas?

---

### Post by Erik1984 on 2012-05-28
Follow-up: I thought of using symlinks as a workaround. So I created a symlink to the desired folder in the micropolis directory (/usr/share/games/micropolis). Problem is the game's built in file browser won't follow symlinks (tried other symlinks I have to test this). So the problem persists.

---

### Post by Davey H on 2012-08-01
I had a go at this game as well. I had no problems running the game, seems stable enough to me. But likewise I can not save it either. I can't select any path in the save as option that it will accept.

---


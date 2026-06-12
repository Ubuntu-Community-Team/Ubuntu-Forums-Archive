---
title: "nexuiz bot game: move teams"
date: 2008-08-21
forum: Gaming &amp; Leisure
---

### Post by sloggerkhan on 2008-08-21
In nexuiz when I set up a local game with some bots, how do I move particular bots do different teams? I can't seem to find any info on this on the nexuiz website.

I want to set up a game where it's 1 v 2 v 2 or similar, but the game always puts the bots in before the player joins meaning player is always on a team. Pretty annoying.

---

### Post by detrate on 2008-08-21
There is a cvar available:

**[bot_vs_human](http://www.nexuizninjaz.com/toolz/cvar/index.php?search=bot)**
set to positive value to make an all-bot blue team, set to negative value to make an all-bot red team, the absolute value is the ratio bots vs humans (1 for equal count)

You can set it by dropping the console (shift+esc) or you can create a cfg file in your Nexuiz data (~/.nexuiz/data) folder called "autoexec.cfg" and put it in there.  autoexec.cfg will execute any custom aliases, cvars or cmds you place inside it.

---


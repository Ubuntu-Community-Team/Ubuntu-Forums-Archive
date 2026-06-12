---
title: "Openarena cheats"
date: 2007-06-06
forum: Gaming &amp; Leisure
---

### Post by ltk5 on 2007-06-06
Do they even exist?

---

### Post by hikaricore on 2007-06-06
If they did, you would know, due to the open source nature of the game.  ^_^

---

### Post by phillipcuk on 2008-09-08
Unfortunately not all of us are savvy at reading code, hence why we ask.

---

### Post by DoktorSeven on 2008-09-08
I certainly hope not.  And if you find one, please don't play on the server I'm on. ;)

---

### Post by scrollheaven on 2009-01-19
OpenArena is based on Quake3 Arena so any Quake3 cheats work with it.

If you open up a copy of pak1-maps.pk3 you'll be able to get all the level map names. Then you can cheat.

For example:

in openarena press the tilde key (~) to open the console

from there type "/devmap aggressor" without the quotes.

You're now in the aggressor map.

Hit the tilde again and type "/god" without the quotes. You are now in god mode.

Enjoy.

---

### Post by donec on 2009-04-23
Thanks but they don't seem to work for me. It appears they work but for instance /god says cheats are not enabled on this server. I am running as single player mode. Any ideas how to get them enabled?

---

### Post by disturbedite on 2009-04-24
> **donec said:**
> Thanks but they don't seem to work for me. It appears they work but for instance /god says cheats are not enabled on this server. I am running as single player mode. Any ideas how to get them enabled?

you have to enable cheats first. look at "Cheat Mode" under "Secrets" here: [http://www.gamefaqs.com/computer/doswin/code/192047.html](http://www.gamefaqs.com/computer/doswin/code/192047.html)

---

### Post by donec on 2009-04-25
> **disturbedite said:**
> you have to enable cheats first. look at "Cheat Mode" under "Secrets" here: [http://www.gamefaqs.com/computer/doswin/code/192047.html](http://www.gamefaqs.com/computer/doswin/code/192047.html)That allows cheats to work but then there are no opponents. It is just like walking through the maps. Any idea on how to fix this?

---

### Post by mattjack809 on 2009-05-23
just hit "esc", then click add bots, select the model, choose the difficulty, and click "add bot" (each time you click it, it adds a bot).

:)

-Matt

---

### Post by crazyfuturamanoob on 2009-05-23
Haven't tested but you might be able to cheat with scanmem.

---

### Post by BarryMead on 2011-01-02
In order to both enable cheats and automatically activate the
proper number of bots for that level do the following

From the menu before selecting a level to play open the console
with ~
type: /sv_cheats 1
type: /devmap aggressor (or whatever map you want to play)
Reopen the console with ~
type: /g_gametype 2
tppe: /map_restart
( map will reload after a countdown )
Reopen the console with ~
type: /god             (to turn on god mode or use any cheat code)

---

### Post by BarryMead on 2011-01-02
Bug Workaround.

openarena has a bug that makes using MODS less than optimally useful.  When you run a MOD within openarena, what happens is that it copies the q3config.cfg file from the
$HOME/.openarena/baseoa directory over to your MOD directory (in my case $HOME/.openarena/Quake3 every time you run the mod regardless of weather the q3config.cfg file already
exists in the mod directory or not.  The proper behavior would be to copy the file if it does not exist, but use the existing file from the mod directory if it already exists.

If you are trying to play original Quake3 levels with the openarena MOD feature, this means that you must re-enter the console command /iamacheater every time you load the game
because is destroys the properly formatted q3config.cfg file relocking all of the levels every time you start the program.

To sum up:  To unlock the levels of the original quake3 game MOD using the openarena engine bring up the console with the ~ key and type /iamacheater. Then you can select any level from the menu.   It is a hassle, but it works.  A better solution is to download the ioquake3-1.36-7.1.i386.run file from the ioquake.org web site and install it.  It does not have the bug.

---


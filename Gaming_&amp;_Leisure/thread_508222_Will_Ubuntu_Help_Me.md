---
title: "Will Ubuntu Help Me?"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by Eezyville on 2007-07-23
OK I'm extremely agitated right now! :evil: I have Windows Vista and the only reason I really use it is because the game developers support it. I hate it! I'm playing one game, Supreme Commander, and it plays like ****! I'm running that game on my laptop which has a dual core AMD Turion 2.0 GHz processor, 2 Gigs of ram and 3 Gigs of virtual memory, and it has a 256 mb graphics card but I always find myself turning the graphics all the way down and cutting th sound to finish a game on an average size map. My friends have this game as well on thier laptops, they don't have dual cores since theirs is older. They can play it just fine! They have XP and I have Vista. What the **** is vista doing to take up half of my processing power and my ram?! 

What i'd like to know is can I play this game in Linux. I'm trying Ubuntu out on my second laptop but please tell my I can play this on Linux and that it runs smoothly. Is there a way to play my other games? I cannot stand Vista, it crashed on me three (3) times in one night. I'm a pc gamer who made a mistake with vista. Help me.:(

---

### Post by themerion on 2007-07-24
That depends usually on how well the game runs in [Wine](www.winehq.com) or [Cedega](www.cedega.com).

You find their info about Supreme Commander here:

Cedega: [http://games.cedega.com/gamesdb/games/view.mhtml?game_id=4616](http://games.cedega.com/gamesdb/games/view.mhtml?game_id=4616)
Wine: [http://appdb.winehq.org/appview.php?iVersionId=7038](http://appdb.winehq.org/appview.php?iVersionId=7038)

---

### Post by Nkari on 2007-07-24
I'd be interested to know how people go with Supreme Commander under Ubuntu, looks like a top game. That was my next project after WoW.

An interesting side note on something I heard the other day, Microsoft is now offering downgrades for a fee to people that got stuck with Vista because it came with their new machine that would really rather have XP on their machines.

---

### Post by NilsHG on 2007-07-24
off topic:
I dont think MS offers downgrades! They want users to go to vista. 
Some resellers, acer, dell etc offer downgrades.

---

### Post by Nkari on 2007-07-24
Clarrification on off topic topic.

Looks like I was misquoted at, a bit of searching revealed that they lifted some sort of restriction that allows people to downgrade customers machines to XP if they have one of two versions of Vista and they supply their own version of XP.

Pretty odd, why can't people just go do that themselves? 

Knew it had to be too good to be true.

So anyway Back on topic who has managed to get The game to run Ubuntu, thinking of shelling out for it but I don't want yet another thing to get me stuck running on my windows partition, its depressing.

---

### Post by lisati on 2007-07-24
> **NilsHG said:**
> off topic:
I dont think MS offers downgrades! They want users to go to vista. 
Some resellers, acer, dell etc offer downgrades.

It might be a matter of opinion, but is moving FROM Vista really a downgrade?

p.s. I haven't used Vista yet.

---

### Post by por100pre1 on 2007-07-24
> **lisati said:**
> It might be a matter of opinion, but is moving FROM Vista really a downgrade?

p.s. I haven't used Vista yet.

I have used Vista, and my answer to you is that moving FROM Vista is surely an UPGRADE.

---

### Post by philter on 2007-07-24
> **Eezyville said:**
> I'm running that game on my laptop which has a dual core AMD Turion 2.0 GHz processor, 2 Gigs of ram and 3 Gigs of virtual memory, and it has a 256 mb graphics card but I always find myself turning the graphics all the way down and cutting th sound to finish a game on an average size map. 

Have you had any problems running other games that are 3D intensive? I know Supreme Commander is definitely a beast of a game on hardware, but a lot of laptop graphics systems run with shared memory. That means that it possibly has a maximum of 256MB of memory usage but probably has only 128MB of ram built into the graphics subsystem. The rest may be coming from your system RAM which is considerably slower than your graphics ram. It is sort of deceiving how they package those things but I've seen that be the cause of issues like this before.

---

### Post by Eezyville on 2007-07-24
> **philter said:**
> Have you had any problems running other games that are 3D intensive? I know Supreme Commander is definitely a beast of a game on hardware, but a lot of laptop graphics systems run with shared memory. That means that it possibly has a maximum of 256MB of memory usage but probably has only 128MB of ram built into the graphics subsystem. The rest may be coming from your system RAM which is considerably slower than your graphics ram. It is sort of deceiving how they package those things but I've seen that be the cause of issues like this before.

Whoa sorry for the 13hr late reply. Works been buisy. But Yeah I can play Need For Speed pretty good on medium graphics. I can also play Battlefield 2 good on medium to low graphics. Supcom intense though. To tell the truth I tried to get rid of Vista before and got XP running on this machine but I had to switch back to vista sadly. Supcom ran great on XP on my laptop though. 

BTW my graphics memory should be 256 dedicated, at least thats what I bought and what I better have.

---

### Post by mccurry on 2007-10-07
Supreme commander works better in XP than vista b/c of vista's graphics issues, it has actually been proven that Wine will render more FPS than Vista will by alost 30 FPS on avg, so go with xp if u need it now, but I havent gotten it to work in Wine yet.  The sound is a known issue it will not work, and the multiplayer hasn't been tested.

---

### Post by mikedep333 on 2007-10-07
> **Eezyville said:**
> it has a 256 mb graphics card(

You're forgetting one important thing. 256 mb graphics adapters can be extremely slow. The easiest way to get a rough idea of performance before directx10 cards came out was to look at the number of pixel pipelines on the adapter.The integrated radeon 7050 with 256 MB of video ram has 2 pixel pipelines. Meanwhile the Geforce 7900 series (usually with 256 MB) has 24 pipelines. That is theoretically 12x the speed without going into more complicated factors. Also, back when I had a laptop with a core 2 duo and radeon x1400 (with 4 pixel pipelines and a total of 384 MB), I still had to turn the the graphics detail all the way down (although I could run at at 1280x800.) The fact that you have dedicated graphics memory means your graphics adapter is likely to be as fast as my radeon x1400.

Also, don't forget that the best way to run a directx9 game like supreme commander is to run it on windows xp with the latest graphics drivers. Updating the the graphics drivers on your laptop if it has an nvidia adapter consists of using the drivers with a modified INF from [http://www.laptopvideo2go.com](http://www.laptopvideo2go.com) . If it is an ATI/AMD one, you need to grab the drivers for a desktop card from ati.amd.com and then use the mobility modder on it found here: [http://www.driverheaven.net/modtool/](http://www.driverheaven.net/modtool/) .

---


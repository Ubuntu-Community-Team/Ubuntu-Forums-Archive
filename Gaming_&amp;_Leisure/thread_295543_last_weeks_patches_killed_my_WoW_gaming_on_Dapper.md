---
title: "last weeks patches killed my WoW gaming on Dapper"
date: 2006-11-08
forum: Gaming &amp; Leisure
---

### Post by Skippyroo on 2006-11-08
One of the things i loved about Ubuntu was that after i installed it for the first time, the game World of Warcraft worked perfectly with no compiling or patching on my ATI RADEON 9600 card. I'd been playing it for about 2-3 months without fault, doing everything from 40 man raids to BGs. Unbelievable and fantastic!!!

All of that changed when i decided to accept the Wine and ATI patches. Unfortunately i installed them both at the same time so it is near impossible for me to figure out which patch to blame (or both). After the patches screwed my system i reinstalled WoW (World of Warcraft), Wine and Dapper in nearly every combination i could think of yet it still won't work.

My symptoms after last week patches are (which worked perfectly before):

  Although i can click on my user interface, i can not click to interact with anything in game (e.g. Players, NPC, Mailbox).

  The game crashes in OpenGL mode if my Character enters an indoor area.

Anyway its a shame considering Dapper worked so well before =(. Is there anyway that i can install old versions through Synaptic or APT-GET? It seems once these packages are upgraded their older counterparts disappear.

---

### Post by YokoZar on 2006-11-08
You can get old versions of Wine from:

[http://wine.budgetdedicated.com/archive](http://wine.budgetdedicated.com/archive)

---

### Post by K.Mandla on 2006-11-08
(I'm just moving this into the gaming forums, where it might get more attention. ;) )

---

### Post by Skippyroo on 2006-11-09
Got it all fixed and worked out it was wine not the fglrx ATI driver.

I reverted to Wine 9.22 instead of Wine 9.24 which is the newest available and it Warcraft just works, and might i say perfectly besides a few frames per second in extremely crowded area's.

For some reason 9.24 crashes before the game even begins. I was trying to install the Ubuntu version which is 9.9 which was causing the mouse doesn't work and the game crashing indoors.

Anyway if any ATI Ubuntu would be World of Warcraft players are reading this, install the Wine 9.22 from wine.budgetdirect.com and the ATI drivers from the Ubuntu package and you should be working without a hitch and without any manual patch or compiling.

---

### Post by hikaricore on 2006-11-09
Guess the phrase "if it ain't broke don't fix it applies a bit here" wine changes a little bit with every release so what works flawlessly in one build may not in another.  Just keep track of your working build and if an upgrade kills your applications just do what you did here and revert back.  Also checking the wine appdb site will keep you up to date on any issues your programs are experiencing with new versions and point you towards possible patches to fix little bits that change here and there in each release.

Hell personally I havn't been able to get wow to launch in opengl mode since 0.9.21 but amazingly d3d works for me somehow since then >.<

Hehe

---

### Post by Ferrat on 2006-11-09
> **Skippyroo said:**
> Got it all fixed and worked out it was wine not the fglrx ATI driver.

I reverted to Wine 9.22 instead of Wine 9.24 which is the newest available and it Warcraft just works, and might i say perfectly besides a few frames per second in extremely crowded area's.

For some reason 9.24 crashes before the game even begins. I was trying to install the Ubuntu version which is 9.9 which was causing the mouse doesn't work and the game crashing indoors.

Anyway if any ATI Ubuntu would be World of Warcraft players are reading this, install the Wine 9.22 from wine.budgetdirect.com and the ATI drivers from the Ubuntu package and you should be working without a hitch and without any manual patch or compiling.

Wine 0.9.24 got better preformance then 0.9.22 

check out 

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

---


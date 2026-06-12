---
title: "SuperTuxKart 0.7 rc 1 - it's like a whole new game"
date: 2010-12-05
forum: Gaming &amp; Leisure
---

### Post by Sealbhach on 2010-12-05
There isn't a deb package but the source is easy to compile. It's got a whole new look, a new graphics engine, new artwork, new GUI. Looks really good:

[http://supertuxkart.sourceforge.net/Main_Page](http://supertuxkart.sourceforge.net/Main_Page)

[http://www.youtube.com/watch?v=tAgDWSfEESA](http://www.youtube.com/watch?v=tAgDWSfEESA)

.

---

### Post by MechaMechanism on 2010-12-06
Yay!  Looks really really good.

---

### Post by TiBaal89 on 2010-12-06
oh that is cool news... i love that game.  new features = new round of addiction to playing! :D

---

### Post by thatguruguy on 2010-12-06
Even better, there's a [ppa for SuperTuxKart]("https://launchpad.net/%7Estk/+archive/dev").

---

### Post by WienerWuerstel on 2010-12-06
The new SuperTuxKart Version looks thousand Times better than any previous Version.

Good Job Dev's :D

PS: Open Source Gaming FTW

---

### Post by DangerOnTheRanger on 2010-12-06
All I can say is =P~ until I get my hands on it...
Just got it!
Now I'm all :D
:lolflag:

---

### Post by Tropcon on 2010-12-11
Okay, has anyone else had this problem? I'm using the ppa and the game installs and runs just fine. However, every now and then, especially when playing multi-player, the keys get kinda' "possessed."
"Possessed" meaning that, for example, my kart will start turning right without my telling it to. It keeps turning right until I push the right arrow (but by that time I'm usually off the track.) It happens to all the navigation keys (eg. randomly turning right or left or putting on the break until I hit the respective key.)
When this problem happens, it happens to both players at once.
It seems that the more AI karts there are, the less likely it is to happen.

Needless to say: this is annoying.

I'm using two USB keyboards, one for each player, so the hardware isn't getting overloaded.

Just wondering if anyone else has had this problem. That will let me know where to look next.

     Thanks!

Edit: Bye the way, I LOVE THIS GAME!!! :D

---

### Post by Arthur_D on 2010-12-11
I'm somewhat involved with the game - though not as a developer. I tried playing with 2 keyboards at the same time earlier today and noticed the same thing. I have no idea what might be going on, but I know of some limitations:
1. As keyboards doesn't have any hardware ID, both keyboards is treated like the same. This means player 1 can't use the same keys as player 2, and is not the fault of STK - it's a hardware limitation.
2. Don't use any of the SHIFT keys, as this will confuse input - say player 1 is driving with arrows and use left SHIFT. Player 2 is using wasd for steering, and will get trouble because player 1 pressing SHIFT makes the wasd keys turn into WASD and change the input values.

If these limitations are taken into account, and you still have problems, please report the bug here: [http://sourceforge.net/tracker/?group_id=202302&atid=981038](http://sourceforge.net/tracker/?group_id=202302&atid=981038)

Otherwise I might report it myself, but I wasn't actually sure if this was reproducible, and as such I haven't done so yet. But if you report it first, I will respond in the report and state that it affects me as well (can't do more tests easily as I don't own 2 keyboards myself).

By the way, thanks for all the positive feedback everyone. :)

---


---
title: "Nexuiz - how to change the difficulty level?"
date: 2008-09-17
forum: Gaming &amp; Leisure
---

### Post by applecookie on 2008-09-17
Hello.

Is there a chance to change the level of the bots in nexuiz. Openarena is much easier and it's possible to tune the level from very easy to impossible. In nexuiz I did not find any option to do so or edit it in a cfg file.

Does anybody have a hint for me?

Thanks.

applecookie

---

### Post by Ozor Mox on 2008-09-17
When you create a game there is an option to set bot skill underneath the number of bots setting. There are quite a lot of levels to choose from.

---

### Post by applecookie on 2008-09-17
Thanks for the hint.

But I mean the singleplayer game (instant action or direct play).

---

### Post by detrate on 2008-09-20
Your dataxxxxxxxx.pk3 (which is just a renamed zip file) in your 'Nexuiz/data' folder contains a config called 'defaultNexuiz.cfg'.  If you extract this from the pack (to your 'Nexuiz/data' folder), you can edit the following cvars:

> 
// general bot AI cvars
set bot_ai_thinkinterval 0.05
set bot_ai_strategyinterval 2
set bot_ai_enemydetectioninterval 0.5
set bot_ai_dodgeupdateinterval 0.1
set bot_ai_chooseweaponinterval 0.3
set bot_ai_dangerdetectioninterval 0.1
set bot_ai_dangerdetectionupdates 64
set bot_ai_aimskill_blendrate 2
set bot_ai_aimskill_fixedrate 15
set bot_ai_aimskill_firetolerance_distdegrees 180
set bot_ai_aimskill_firetolerance_mindegrees 2
set bot_ai_aimskill_firetolerance_maxdegrees 45
set bot_ai_aimskill_mouse 1
set bot_ai_keyboard_distance 250
set bot_ai_keyboard_treshold 0.57
set bot_ai_aimskill_offset 1
set bot_ai_aimskill_think 1


I'm not sure if this will work for campaigns because I think that uses another config but it should work for instant action.

---

### Post by sloggerkhan on 2008-09-20
you might be able to use console to change bot skill ingame.
Not sure about this though.

---

### Post by detrate on 2008-09-20
> **sloggerkhan said:**
> you might be able to use console to change bot skill ingame.
Not sure about this though.

Changing the options in console will do the same thing as above but make it "session based".  That is, it won't save the next time you restart Nexuiz unless you explicitly tell it to save the changes.

---


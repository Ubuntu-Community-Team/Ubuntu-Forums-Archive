---
title: "WoW using Cedega"
date: 2005-12-18
forum: Gaming &amp; Leisure
---

### Post by hoobadoo on 2005-12-18
I installed World of warcraft using TrabsGaming cedega. When I run wow I get into the game and all the text is small and blurry and I can not select any Player/NPC. I've Seen a few other threads but they all have used wine, can anyone help me please.

---

### Post by hoobadoo on 2005-12-18
Ok I have the problem fixed, but now whenever I click on a person it freezes for about 1 second. Is there anyway I can fix that, it gets really annoying when your trying to do some quick fighting.

---

### Post by Kadin2048 on 2005-12-23
Apparently there are some problems with WoW and Cedega regarding clicking ... ?

I have not used, but I did hear it mentioned on the Cedega forums. You might want to check there, IIRC there is a workaround, although it will mess up other games and/or may lower your framerate.

I'd be interested in your opinions on how it works once you apply all the workarounds and whatnot, since I was thinking of getting Cedega specifically for WoW.

---

### Post by awakatanka on 2005-12-23
[QUOTE=Kadin2048]Apparently there are some problems with WoW and Cedega regarding clicking ... ?

I have not used, but I did hear it mentioned on the Cedega forums. You might want to check there, IIRC there is a workaround, although it will mess up other games and/or may lower your framerate.

I'd be interested in your opinions on how it works once you apply all the workarounds and whatnot, since I was thinking of getting Cedega specifically for WoW.[/QUOTE]
There where some problems with it, but there is a solutions for it that are working for some. For me it this 1 worked.

1) This workaround may not work on all distros, may prevent other games (such as Half-Life 2) from running but should not cause a speed decrease.
open a console/terminal window and run
export WINEPRELOADER_SETVALEGACY="no"
then launch Cedega or Point2Play from the same terminal window.
This would need to be set each time you open a new terminal window to play the game.

[http://transgaming.org/forum/viewtopic.php?t=3149](http://transgaming.org/forum/viewtopic.php?t=3149)

Only problem i had was getting it to download the patches. but thats also solved. I hate it thats there no native linux solution so much easier ;). Evry new wow patch you have to hope it still works.

---

### Post by AnimalMother on 2005-12-23
I hate to have tell you this after paying for cedega but WoW works flawlessly under wine(9.3) with the mouse fix patch applied to its source code.  I have been playing for two days-hours on end-without flaw.  If you are interested I will post the patch. It even logs out and exits the game without freezing up. Before this I used cedega with WoW, but graphics and funtionality are better with wine (that is until the next WoW patch screws everything up again).  I was also getting a segmentation fault with cedega every now and again.  This has not happened under wine.

---


---
title: "EVE Online Performance"
date: 2008-05-22
forum: Gaming &amp; Leisure
---

### Post by Skeet on 2008-05-22
I am wanting to play EVE Online on Hardy with the following specs.

Intel Core 2 Duo E6550
Nvidia GeForce 8800GT 512MB
2GB DDR2 Ram

I am currently running the EVE Linux client in Cedega and i'm getting inconsistant 50-90 frames and its very jumpy.

Is there a way of running it differently to increase performance? With its current state I cannot enter PVP or PVE situations because it cannot handle it.

---

### Post by NR1224 on 2008-05-22
I was under the impression that EVE had a full native linux client, no Cedaga/Wine/Crossover required.If not, check your internet connection. That is what causes bad gameplay on my linux computer.

---

### Post by Skeet on 2008-05-22
The eve linux client requires Cedega engine to run. Its not directly imported into Cedega, but it uses it.

---

### Post by NR1224 on 2008-05-22
<snip> are you using wireless internet or wired? also, where are you getting lag?, all over or only in certain places? Maybe just try lowering all the settings and see if that helps. Sorry I cant be any more specific, but i have only played the windows version, and only the trial at that.

---

### Post by Cappy on 2008-05-22
> **NR1224 said:**
> I REALLY dislike people like this ^ jerk, selling stuff on a user forum...:mad:, Anyway, are you using wireless internet or wired? also, where are you getting lag?, all over or only in certain places? Maybe just try lowering all the settings and see if that helps. Sorry I cant be any more specific, but i have only played the windows version, and only the trial at that.

He's not selling anything.

Eve's "native" client is just Cedega + Eve Online.

---

### Post by NR1224 on 2008-05-23
I need to clarify, there was a computer generated messedge advertising WoW accounts that was since deleted when you guys read it. It made it appear as if I had called the thread starter a jerk, but  I swear I was not. I apologize for the trouble and to the thread starter, I was not directing that comment at you.

---

### Post by Perfect Storm on 2008-05-23
Okay, found it in the jail. Your infraction will be reversed.
Do not reply or interact with a spammer, but use the report button instead and we'll send him to kingdom come.
Then such misunderstandings can be avoided.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by Skeet on 2008-05-25
I'm not a spammer? It was a genuine question. Wtf?

---

### Post by Sammi on 2008-05-25
> **Skeet said:**
> I'm not a spammer? It was a genuine question. Wtf?Read the two posts right above yours :popcorn:

There was a spam message right above NR1224's first message, that got deleted pretty quickly. 

That was what he was referring to, not you:lolflag:

Anyway try running it in Wine. It's far more mature than Cedega, because it gets more quality development. Cedega is really nothing more than 5 year old version of Wine dressed up in fancy clothes. Wine is even able to run the premium client decently.

Instructions:
Classic client: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10136](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10136)
Premium client: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971)

If you want a GUI for Wine, then buy Crossover Games: [http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/) (it has a trial)

---

### Post by SpudNoSkill on 2008-05-25
I'm running the native Eve Client with premium graphics enabled the same as I do in windows. Frame rates are ok in space and provided you don't zoom in too far you'll be ok most of the time.

However that said there are problems with the client lagging when loading a new grid (for PvP or PvE). This has about a 50% increase in lag over the normal client in Eve. I'm not sure why this is but it does make loading into a new situation a problem ..... worse than that when at a fully configured Deathstar PoS I dropped to 10 FPS even when there were no ships present... this was against over 100FPS on Windows. I haven't found out a way to improve this yet but I'm optimistic that I'll find a way to improve things soon.

System wise I have the same CPU and the same graphics card .... If I get the performance up I'll let you know.

---

### Post by Sammi on 2008-05-25
> **SpudNoSkill said:**
> I'm running the native Eve Client with premium graphics enabled...What are you using, Wine?

---

### Post by Skeet on 2008-05-25
I was using the official eve linux client, I think it runs in Cedega. I will try using Crossover and post my results

---

### Post by Skeet on 2008-05-26
I installed the Crossover trial, used it to install EVE Classic Client. It installed fine, patched fine. But when I try to run it, the splash screen pops up, it hangs on that, then disappears after a while. The game doesn't even pop up?

---

### Post by Sammi on 2008-05-26
> **Skeet said:**
> I installed the Crossover trial, used it to install EVE Classic Client. It installed fine, patched fine. But when I try to run it, the splash screen pops up, it hangs on that, then disappears after a while. The game doesn't even pop up?

Found this here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10136](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10136)
> If you can't get past the splash screen, try installing the Premium patch and disabling premium content. 
     
    
   If it doesn't work you might want to start with a new ~/.wine directory.
   - run "wine winecfg" to setup/configure your wine install (mainly sound driver)                                                                      
- you can copy the Eve folder into ~/.wine/drive_c/ or install from scratch. (try without the cache folder first)                                                                      
- copy arial.ttf to ~/.wine/drive_c/windows/fonts/      (install ms corefonts package and then search for arial.ttf on your disk)                                                                 
- install the d3d9x_30.dll by running the RedistD3DXOnly.exe in the bin dir                                                                      

---


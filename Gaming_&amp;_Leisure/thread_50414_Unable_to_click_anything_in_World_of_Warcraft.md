---
title: "Unable to click anything in World of Warcraft"
date: 2005-07-20
forum: Gaming &amp; Leisure
---

### Post by GoneWacko on 2005-07-20
Hi all :)

After a quick search on the forums I have not found any information about this, but I hope there is information available none the less:
I am finally able to run my World of Warcraft under linux using Cedega.

Everything is fine and dandy. It installed without problems, it patched without problems, it runs without problems. Or actually, there is one tiny problem:

I can't click any NPCs, mobs or objects in the game :( All the interface stuff works (buttons, items, etc) but in the actual gameworld, I can't even hover over anything (when I move my mouse over, for example, an NPC, the NPC does not glow slightly to make clear that it's being hovered over)

This is rather irritating, because I can't play the game if I can't select NPCs :)

I can target people with /target <name>   and probably using TAB to target mobs would also work, but if I can't click on a questgiver or vendor, the game gets very boring to play :-D
Does anyone have a clue what might be causing this? I really want to get rid of Windows once and for all, but if I can't play WoW on Linux, I'll be forced to at least have a small windows partition :(

---

### Post by Domhnull on 2005-07-20
[Transgaming Forums - work around](http://transgaming.org/forum/viewtopic.php?t=3149&sid=ad258914a9a2c11baf1ab86a0b7abfbe) 

This has been an issue.  I found their first mouse solution to work fine for me.

EDIT:  Note, this isn't a fix - you have to do it each time.  Hopefully Transgaming will get it actually fixed soon.

---

### Post by tyme on 2005-07-20
if you go into the config file for cedega (different place depending on if you use Point2Play or command line cedega) and search for MemoryLayoutOverlay, uncomment that line, it should fix this.

---

### Post by GoneWacko on 2005-07-20
Thanks! I'll give it a shot :)

I forgot to check the TransGaming forums :-p

---

### Post by dickohead on 2005-08-28
[QUOTE=Domhnull][Transgaming Forums - work around](http://transgaming.org/forum/viewtopic.php?t=3149&sid=ad258914a9a2c11baf1ab86a0b7abfbe) 

This has been an issue.  I found their first mouse solution to work fine for me.

EDIT:  Note, this isn't a fix - you have to do it each time.  Hopefully Transgaming will get it actually fixed soon.[/QUOTE]
 And if you're using wine to play WoW and have the same issue? Both of those workaround don't work... has anyone got a fix when using wine?

---

### Post by mailbox on 2006-07-01
I'm having the same problem, only I can't find the wine config file to try out #2... any ideas?

---

### Post by Rushed Luncheon on 2006-07-21
I'm running WoW in wine, and I have exactly the same problem. Any ideas for wine fixes?

---

### Post by xfaith on 2007-03-27
Ubuntu - Wow - Wine - Nivida - OpenGL

Same trouble.  Unable to click any NPC's or mobs.

Any help is appreciated. 

Xfaith

---

### Post by ArgAthens on 2007-04-20
I was able to click before upgrading running while running WoW in direct3d mode.  After upgrading I'm unable to click on anything regardless of mode.

Also I tried 'export WINEPRELOADER_SETVALEGACY="no"' to no avail.

Any help would be appreciated!

---

### Post by ArgAthens on 2007-04-23
Running it with the -windowed switch has me clicking away!

---


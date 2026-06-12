---
title: "NWN memory corruption"
date: 2006-06-24
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2006-06-24
Well I've played alot of nwn on Dapper but now I'm unable to load games even on a fresh nwn install: This is what shows up -

 sh /home/orion/.Games/startNWN.sh
*** glibc detected *** malloc(): memory corruption: 0x0ea4c240 ***
./nwn: line 12:  8509 Aborted                 ./nwmain $@

when I try to load a game.

Is it my hardware that starting to failing or is a bug somehow.


Thanks.

---

### Post by seth0x2b on 2006-06-24
Don't know if this will help you, but it might worth looking into:
[http://nwn.bioware.com/forums/viewtopic.html?topic=466479&forum=72&sp=0](http://nwn.bioware.com/forums/viewtopic.html?topic=466479&forum=72&sp=0)

Cheers and good luck

---

### Post by AngryKidJoe on 2006-06-24
It also wouldn't hurt to run some tests on your memory as well. Best to get that out of the way instead of having the possibility lingering around.

---

### Post by Perfect Storm on 2006-06-25
Memory checked. No errors.

Also tried as suggested in the link, which freezes my computer. But I think the reason in the link is correct. Anyway why in hell is debugging enable in glib anyway? It's slow down the system and is to no use for normal users.

But I also guess that my tinkering/tweaking of Ubuntu might activated the strange error, to bad I've made so many tweaks I'm unable to locate which it is. Oh well I've backup my stuff and going for a reinstall. If no luck either there I'm heading back to breezy.

---

### Post by Perfect Storm on 2006-06-25
Okay. Reinstalled Ubuntu and nwn. Same issue. But but but....I found the thing that causes the crash and the memory corruption. It's my homemade character picture. Somehow I've been unprecise with size of the picture, but I thought it was okay since it worked ingame, but nwn couldn't handle it when exporting the .tga file to the save folder (weird).

So I'm down to two options:
1. remake my character pictures.
2. Everytime I want to load a game 've to go to the save folder and re-exchange the .tga file, then it works.

Problem solve (kinda).

---

### Post by seth0x2b on 2006-06-25
Well it's nice that you've figured it out.You probably know how to set up your custom image, but here's the official custom portrait HowTo.
[http://nwn.bioware.com/builders/portraits.html]("http://nwn.bioware.com/builders/portraits.html")
You might wanna follow they're steps if you haven't already.


> **The bottom portion of the image MUST be blank and unused.** If it is not blank, your computer will light on fire and explode when you try to save your game -- er, well, or it might just crash.

Hope it helps.Cheers

---

### Post by Perfect Storm on 2006-06-25
Aye, I know that :), but I did it in a hurry :-#  so it could easely slipped.
Back to gimp.


Just grab a picture to show it work :mrgreen: 
Gonna build me Pale master (lvl30), fighter(lvl4), Wizard(lvl6)

---


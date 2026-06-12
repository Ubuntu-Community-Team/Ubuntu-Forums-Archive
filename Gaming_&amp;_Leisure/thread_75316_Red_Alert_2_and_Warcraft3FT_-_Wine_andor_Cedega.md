---
title: "Red Alert 2 and Warcraft3:FT - Wine and/or Cedega?"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by meastp on 2005-10-13
Hi!

Just installed Breezy, and so far, so good. I was wondering if warcraft3:frozen throne and red alert 2 works flawlessly with either wine or cedega (both?). You see, I play these games on LAN with friends a couple of times a year, and would like to have them working in ubuntu.

---

### Post by KingBahamut on 2005-10-13
I recommend Cedega for both. 

I know for a fact that Warcraft3 works flawlessly. 

Red Alert 2 runs moderately to fairly well under Cedega also.

---

### Post by withoutclass on 2005-10-13
[QUOTE=KingBahamut]I recommend Cedega for both. 

I know for a fact that Warcraft3 works flawlessly. 

Red Alert 2 runs moderately to fairly well under Cedega also.[/QUOTE]

ahh, well flawlessly depends a lot on your system too.  Running an ATI card like I do really screws up the whole situation.  The install for wc3:tft went perfectly fine(cedega), but even with configuring the fglrx driver and getting 3D acceleration to work, the game was very slow and choppy, to the point where it was unplayable

---

### Post by Jad on 2005-10-13
Red alert 2! now you are talking guys

---

### Post by jecos on 2005-10-13
[QUOTE=withoutclass]ahh, well flawlessly depends a lot on your system too.  Running an ATI card like I do really screws up the whole situation.  The install for wc3:tft went perfectly fine(cedega), but even with configuring the fglrx driver and getting 3D acceleration to work, the game was very slow and choppy, to the point where it was unplayable[/QUOTE]

War3 should work just fine under cedega and fglrx..  put -opengl as a command in cedega

---

### Post by withoutclass on 2005-10-13
[QUOTE=jecos]War3 should work just fine under cedega and fglrx..  put -opengl as a command in cedega[/QUOTE]

aight, i will test it again, just that i dont like leaving my driver as fglrx because when they produced the new one they left out 1280x800 monitor sizes, and the old driver isnt compatible with breezy

---

### Post by gil-galad on 2005-10-13
Warcraft 3 works perfectly under wine if you use the -opengl switch.

---

### Post by mojo on 2005-10-13
[QUOTE=withoutclass]aight, i will test it again, just that i dont like leaving my driver as fglrx because when they produced the new one they left out 1280x800 monitor sizes, and the old driver isnt compatible with breezy[/QUOTE]

If this doesn't resolve the lag of the game, then you should check your driver. Make sure you install libstdc++5, I got lag performance with fglrx w/o libstdc++5.

---

### Post by meastp on 2005-10-14
Well, I guess I'll have to try it out for myself, then! :) I have a nvidia-card, btw. RA2: IPX/LAN works too? It'll have to, as there is no point in playing single player on a LAN ;)  (I've heard a lot of fuss about IPX-support in older C&C-games, thats why I'm nagging a bit.)

---

### Post by Trab on 2005-10-14
anyone gotten multiplayer in RA2 to work? and anything about yuri's revenge? i know a while ago i tried to get it to work, and was barely able to isntall YR but it didnt work.... thats like the LAST thing i use windows for.... any advice?

---

### Post by meastp on 2005-10-15
I haven't tried it yet myself, because I'm having trouble installing it: [http://ubuntuforums.org/showpost.php?p=414074&postcount=7]("http://ubuntuforums.org/showpost.php?p=414074&postcount=7")


You may want to have a look at [http://transgaming.org/forum/viewtopic.php?t=212&postdays=0&postorder=asc&highlight=red+alert+2&start=0&sid=193ce1571b6cacfcd59b7ede7231bbcd]("http://transgaming.org/forum/viewtopic.php?t=212&postdays=0&postorder=asc&highlight=red+alert+2&start=0&sid=193ce1571b6cacfcd59b7ede7231bbcd")

---

### Post by jeffreyvergara.NET on 2005-10-15
im playing Warcraft 3 TFT: DOTA using cedega and it's works perfectly even without -opengl

---

### Post by gtr225 on 2007-06-20
> **Trab said:**
> anyone gotten multiplayer in RA2 to work? and anything about yuri's revenge? i know a while ago i tried to get it to work, and was barely able to isntall YR but it didnt work.... thats like the LAST thing i use windows for.... any advice?Under Cedega I'm able to install and run Red Alert 2, but when I try to install Yuri's Revenge I get an error that says "Red Alert 2 not detected".

---


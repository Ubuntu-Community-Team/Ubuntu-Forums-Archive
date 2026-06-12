---
title: "Minecraft keeps pausing"
date: 2011-05-18
forum: Gaming &amp; Leisure
---

### Post by pengper on 2011-05-18
Only got Ubuntu yesterday- this is a very new system to me, but I'm loving it and have the knack it seems.

One of the first things I did on it today was open up [www.minecraft.net](www.minecraft.net), login, and try to play in browser. No such luck. The java window just didn't open. I've opened the Software Centre and installed most things under the search 'Java' (within reason).

So I tried downloading and running the .jar- didn't work. 

So I got an installer off of [http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735) - this works completely. Until- playing away happily, much faster than Windows was, until- clicks on tree trunk again, and Minecraft pauses. Unpauses and tries again. Yep, this block of wood makes minecraft pause. Wanders off and finds a neat cliff to put a house in, clicks on earth- pauses. 

Minecraft now pauses on block click.

In the open Terminal, this message was displayed a tonne of times- Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13) . Finally, it stated "Linux plugin claims to have found 0 controllers". Mean anything to anyone?

---

### Post by Fluffgar on 2011-09-27
I have no answers as yet but you're not the only one with this weird problem. I just encountered it today :(

---

### Post by ferrarirs on 2011-09-29
It works fine for me.

---

### Post by cynt_ on 2011-09-30
Same here. Also, it's reaaaally laggy since 1.8

---

### Post by cynt_ on 2011-09-30
I figured it out. 
1 - Download [http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.7.1/lwjgl-2.7.1.zip/download](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.7.1/lwjgl-2.7.1.zip/download)
2 - Overwrite the files in .minecraft/bin with the ones in the jar folder from the downloaded file.
3 - Overwrite the files in .minecraft/bin/natives with those /native/linux folder of the downloaded file.
And you're ready to go ;)

---

### Post by daflad on 2012-04-29
Ok so i also had the same problem of every time i tried breaking boxes it paused i found a much simpler answer change break block to a keyboard button ( I notice that even with no action set to mouse button one holding it down still can pause it)  i personally use the z button. Just thought i'd mention that its the fastest way around the problem that i have found.

---


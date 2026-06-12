---
title: "WoW locks up while loading"
date: 2007-09-10
forum: Gaming &amp; Leisure
---

### Post by Dgc2002 on 2007-09-10
I've read several reports of the same issue, none of which have resolved the problem...I don't expect anything else here because it seems a mystery but i might as well try :)

So, i played wow fine for the first day of my linux life. But now while trying to "Enter World" On my char(Who is in ZF) it freezes while loading, at the very end of it too :P The same happens to my low level war who is outside org. I havn't a clue why this would happen. i was suspicious that it was a busy area issue, so i moved my char out of gadgetstan into the desert in tanaris and still couldn't log in. But about 45 mins later i could log in...its odd.

I'm wondering what might cause this problem, what are some steps i can take to possibly solve this issue...i just wanna level my lock!! =D

Ty in advance for the help

Oh and some hardware information

AMD Athlon 64 3200+
nVidia Geforce 6800 
Not sure what else would matter, and i can't seem to find other specifics in the hardware display that comes with Ubuntu Fiesty(sp)

---

### Post by Nubsauce on 2007-09-10
It may just be an issue with WoW itself.

Not sure if it's the same issue I have on Windows(I'm too lazy and overworked to configure it properly to maximize my FPS so I just play in windows for now..  :p ) then it's probably just WoW related.

What happens to me on windows is that it will randomly decide to crash WoW after loading completely but before it actually drops you in game.

So, if you're experiencing anything like that I'd bet it was related to Blizzards cracker jack programming team of monkeys.

---

### Post by Dgc2002 on 2007-09-10
Not its not like that, thank you for the reply tho.

It simply stops responding after i hit "Enter World" and it has the loading screen with the tip, it gets to the end then just stops. i have to close it and force quit to get out of it

---

### Post by Nubsauce on 2007-09-11
Well, that's pretty much what happens to mine except under Windows it crashes properly.  Under Linux, it might lock up when it crashes before the client's own system can catch the error.

If you use any mods try removing them and deleting your WTF folder and see what happens.  I just copied my WoW folder over to my linux partition so it's the same install that crashes..  I guess we'll see what happens, getting ready to test now.

---

### Post by ExSuSEusr on 2007-09-11
I don't know if this will help or not.  But, check your version of Wine.  I had locking up problems until I changed to wine 0.9.43.  After that I have no issues with getting in the game.

---

### Post by Dgc2002 on 2007-09-11
> **ExSuSEusr said:**
> I don't know if this will help or not.  But, check your version of Wine.  I had locking up problems until I changed to wine 0.9.43.  After that I have no issues with getting in the game.

Thanks, i'm working on that now. I had to use .43 because the 64bit .44 download...just doesn't work. I'm going to try the non-64bit version of .44. I'll report back, i sure hope this works :P i'm a 49 lock and rested to 50 so i'll get my felguard :P

---

### Post by Stolen on 2007-09-11
> **Dgc2002 said:**
> Thanks, i'm working on that now. I had to use .43 because the 64bit .44 download...just doesn't work. I'm going to try the non-64bit version of .44. I'll report back, i sure hope this works :P i'm a 49 lock and rested to 50 so i'll get my felguard :P

0.9.44 has a problem as well (sometimes freezes at login, always freezes on exit), try 0.9.43.
WineHQ has a bug on the 0.9.44 with patches to fix it already submitted, so it should be fixed in the next release (or 2).

---


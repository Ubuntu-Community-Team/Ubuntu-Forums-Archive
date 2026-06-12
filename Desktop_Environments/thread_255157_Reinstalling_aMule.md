---
title: "Reinstalling aMule"
date: 2006-09-11
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-11
I had my machine crashing a few days ago, but I could backup my aMule folder before formatting.

When I now install aMule, but then exchange the Temp folder and the configration files and so with the old ones, aMule won't run.

How can I save my old unfinished downloads and my credit?

Thanks

Gabriel

---

### Post by ijanos on 2006-09-11
It should run.
Try to run it from terminal and see whats the problem.

---

### Post by GabrielWolff on 2006-09-11
Right after boot, this is the answer I get:
```
gabriel@gabriel:~$ amule
Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.
gabriel@gabriel:~$
```
How come? I surely didn't start the application - it can't be running. Or do I understand it wrong?
Gabriel

---

### Post by ijanos on 2006-09-11
Hmm strange.
Try this: remove your old config from .aMule, make sure you can start and use amule. Now close it and copy back some files (preferences, the temp and some  other stuff) from your old config start amule and if theres no trace of your old settings close it and copy the other files one by one. Start with the files you know (or you could guess) what it does.

---

### Post by mlind on 2006-09-11
Try removing ~/.aMule/muleLock file and try again.

---

### Post by ijanos on 2006-09-11
Hey that makes sense :D

---

### Post by GabrielWolff on 2006-09-12
Great, works like a charm :D 
 
Thanks

Gabriel

---

### Post by stuart_75 on 2006-10-21
> **mlind said:**
> Try removing ~/.aMule/muleLock file and try again.

This works for me. If I shut down Ubuntu without closing amule first, then amule gets screwed up and wont work.

Removing the mulelock file works a treat.

---


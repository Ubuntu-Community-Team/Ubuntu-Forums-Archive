---
title: "How do I get Unreal gold to work"
date: 2006-04-29
forum: Gaming &amp; Leisure
---

### Post by shade11 on 2006-04-29
Hey all, I have had very little problems for awaile with Ubuntu. But a new problem has arose, I want to install Unreal Gold.

I looked it up on google and found an Icclus.org installer. The installation had gone exceptionally well until I ran unreal.

It said that the UNREAL_DATA_PATH was needed.

So I went to "/usr/local/bin/unrealgold" and added 
```
export UNREAL_DATA_PATH=/usr/local/games/unrealgold/System
``` to it.

I ran it again and came up with this error message.
```

./unreal-bin: error while loading shared libraries: Engine.so: cannot open shared object file: No such file or directory
```

---

### Post by Thirsteh on 2006-04-29
I would suggest trying 'locate Engine.so', and changing or adding the necessary directory path.

---

### Post by shade11 on 2006-04-30
I have looked for engine.so and it isn't anywhere on my filesystem.

---

### Post by leech on 2006-04-30
Did you install Unreal Tournament first?  That's a requirement.  Unreal was never ported to Linux, Unreal Tournament was the first Unreal engine game that was.  I know it works, 'cause I have it running on my laptop.  

Once you get it so it'll load, hopefully you don't have a speed stepping processor, otherwise it'll run at a billion frames per second :D

I'll see if I can find that script again, but basically what would happen is that your computer will be at the lower speed, when UT would load, so it'd do all of it's calculations based on that.  But then your processor jumps up after something hits the 3D hardware, so UT suddenly runs like it's on SPEED!

If you have that problem, just ask and I'll post the script.

Leech

---

### Post by opt1k on 2009-11-30
This is an old thread; but for anyone searching the correct way to execute it is as follows:

$  UNREAL_DATA_PATH=/usr/local/games/unrealgold/System unrealgold

---


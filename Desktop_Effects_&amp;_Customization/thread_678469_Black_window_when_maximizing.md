---
title: "Black window when maximizing"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by the lah on 2008-01-25
Every time i maximize a window parts of the window turn black for about 1-2 seconds then it goes away. Its starting to bug me and i don't know how to fix it. Please help.
- Using Compiz Fusion with NVIDIA GeForce2 MX with gutsy gibbon 

Thanks!

---

### Post by mouseboyx on 2008-01-25
This is natural mine does it to if I am using more than 50% of my ram or CPU.  But never more than 1 second.  Basically no way to fix this.

---

### Post by the lah on 2008-01-26
I found this thread [http://ubuntuforums.org/showthread.php?t=587927&highlight=black+windows]("http://ubuntuforums.org/showthread.php?t=587927&highlight=black+windows")
Which shows a solution in this site [http://www.deepnerd.com/node/82]("http://www.deepnerd.com/node/82")
It says
 "    1.  follow through on setting up emerald themes
   2. install nvidia-glx-new, nvidia-new-kernel-source and nvidia-glx-new-dev (for good measure - not sure if the last two are really needed)
   3. reboot (again not really needed if you know what you're doing, but it can't hurt, can it? go grab a beers)
   4. enable eye candy (system>preferences>appearance>visual effects)
   5. it should "just work". Now try to break things to prove your confidence. "

Is it safe to try this? And what do they mean by setting up emerald themes? I don't even have the system>Preferences>Emerald Theme Manager.

---

### Post by FuturePilot on 2008-01-26
It's a bug in the Nvidia Driver. There's really nothing to fix it until Nvidia does. 
You could try Compiz with indirect rendering. Your mileage may vary
```
compiz --loose-binding --indirect-rendering
```

---


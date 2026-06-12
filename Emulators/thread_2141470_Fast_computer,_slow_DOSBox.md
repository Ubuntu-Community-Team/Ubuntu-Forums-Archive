---
title: "Fast computer, slow DOSBox"
date: 2013-05-02
forum: Emulators
---

### Post by Maximus559 on 2013-05-02
I'm running DOSBox 0.74 on Xubuntu 12.10 64-bit, and have run into some serious performance issues.

My CPU is an i5-3210M, but I'm only getting about 30 fps in the Quake timedemos. I've seen slower machines get 100+ fps. Other games are running sluggishly as well.

My DOSBox config file is more or less stock. Any ideas as to what might be causing this? (I'm tempted to blame the 64-bit OS, but that's just a wild guess.)

---

### Post by kostkon on 2013-05-03
> **Maximus559 said:**
> My DOSBox config file is more or less stock.
What changes have you made?

---

### Post by Maximus559 on 2013-05-03
> **kostkon said:**
> What changes have you made?

fullresolution=1366x768
output=overlay
aspect=true

Setting these back to default makes no difference. Haven't touched any CPU or sound settings.

---

### Post by kostkon on 2013-05-04
> **Maximus559 said:**
> fullresolution=1366x768
output=overlay
aspect=true

Setting these back to default makes no difference. Haven't touched any CPU or sound settings.
Why not openglnb for output. It will nicely scale your game, like overlay does, but will also be hardware accelerated.

Also, since it is a demanding game, try following the tips outlined [here]("http://www.dosbox.com/wiki/Performance"), like setting the cpu core to dynamic and cycles to max.

---

### Post by Maximus559 on 2013-05-04
> **kostkon said:**
> Why not openglnb for output. It will nicely scale your game, like overlay does, but will also be hardware accelerated.

Also, since it is a demanding game, try following the tips outlined [here]("http://www.dosbox.com/wiki/Performance"), like setting the cpu core to dynamic and cycles to max.

That's good to know about openglnb; unfortunately, it didn't make a difference in this case. Neither did core=dynamic or cycles=max.

---


---
title: "Installing ubuntu 8.10 64bit on Inspirion 1420"
date: 2008-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by frbe0101 on 2008-11-28
I replacing my harddrive on my inspiron 1420, presently its running 8.04 (32bit), I want to install 8.10 64bit, are there any problems I should know about ahead of time?

---

### Post by iggykoopa on 2008-11-28
with 64 bit if you want to control the fans you will have to use dellfand, theres some guides on this forum i8k isn't available for 64 bit yet. Also I would recommend getting the new 64 bit flash beta, there isn't an installer but all you need to do is put the libflashplayer.so in ~/.mozilla/plugins . Other than that it runs perfect for me.

---

### Post by frbe0101 on 2008-11-28
> **iggykoopa said:**
> with 64 bit if you want to control the fans you will have to use dellfand, theres some guides on this forum i8k isn't available for 64 bit yet. Also I would recommend getting the new 64 bit flash beta, there isn't an installer but all you need to do is put the libflashplayer.so in ~/.mozilla/plugins . Other than that it runs perfect for me.

what do you mean about the fans, they aren't temp controlled in 64bit?

---

### Post by iggykoopa on 2008-11-28
from my experience they aren't temp controlled on any version of ubuntu unless you specifically enable it... the bios just keeps the fans going at medium speed all the time(on 32 bit you can either use i8k to control the fans or dellfand, on 64 bit only dellfand works but its easy to set up) this thread [http://ubuntuforums.org/showthread.php?t=877611&highlight=dellfand](http://ubuntuforums.org/showthread.php?t=877611&highlight=dellfand) shows how to set it up.

edit: oh and just to let you know that most people report even with those two controlling the fan it surges at high speed....happens to me too, it'll run high speed for a few seconds then the bios tries to take back over and slows it to mid speed, then dellfand speeds it up again and so on, but at least it still keeps the laptop cooler

---


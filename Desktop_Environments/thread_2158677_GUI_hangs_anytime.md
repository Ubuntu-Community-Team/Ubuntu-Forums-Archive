---
title: "GUI hangs anytime"
date: 2013-06-30
forum: Desktop Environments
---

### Post by nachollica on 2013-06-30
Hi all! I'm using Ubuntu 13.04 64bit. I use compiz because I need the accesibility features (it's an important detail). While I'm using the desktop normally (using web browser, watching videos with totem, listening music, etc.) it randomly hangs for a moment. The screen freezes for 1 second approx. Sometimes the audio also hangs, sometimes not. I don't know if it's a problem of X Org, the hardware, drivers. etc.
When I had Ubuntu 12.04, I had another problem (also using compiz). The compiz hung, the screen froze and then all restores but with a crash message window and compiz reset (no magnifier and no negative windows - the accesibility features I use). So I think maybe the issue is because the buggy compiz.

My PC:
Mother: Gigabyte GA-MA770-UD3
Graphics: NVIDIA 9500 GT
Graphic drivers: (I tried various, but the issue persisted). Nouveau and NVIDIA privative drivers.
CPU: AMD Phenom II x2 550
RAM: 1GB Corsair + 1GB Corsair + 2GB Kingston (mid-range RAMs, normal latencies)
SO: Ubuntu 13.04 64-bit

Thanks a lot!

---

### Post by dino99 on 2013-06-30
compiz have many known issues ; so its important to reset it if you have made some tweaks. Always deactivate all the options you does not really need. The best way to find the faulty setting/plugin is to only activate one plugin at a time, to know if you have to blame it.

from a terminal, run: ```
dconf reset -f /org/compiz/
```

---

### Post by nachollica on 2013-07-01
Thanks dino99! I will try it and test the results :) If someone has another idea, please comment. Greetings!

---

### Post by nachollica on 2013-07-09
Hello! The problem is (at the moment, haha) solved. I did two things, and I'm not sure what was the solution. I deactivated the compiz options and started to activate one plugin at a time. At this moment I have the same plugins that I had when the computer hung, but maybe there is a little setting in some plugin that I didn't realize that exists. The other thing I did is to download the official drivers from NVIDIA web for my videocard. Before I was using the drivers that Ubuntu has. I believe that the solution was the drivers, but not sure.

Thanks to the forum for providing this space! Regards!

---


---
title: "Unity Dash and Launcher Disappeared!"
date: 2012-06-06
forum: Desktop Environments
---

### Post by gamehero77 on 2012-06-06
I launched Eclipse on Ubuntu 12.04 and the Unity Launch and Dash suddenly disappeared. I could mouse over where it had disappeared and I could still interact with the invisible dash and launcher. I don't know why its doing this or how to fix it. Here's my system info:
Memory: 2.7 GB
Processor: AMD Athlon(tm) Processor TF-20 
Graphics: VESA: RS780MN
OS Type: 32 bit

---

### Post by wilee-nilee on 2012-06-07
> **gamehero77 said:**
> I launched Eclipse on Ubuntu 12.04 and the Unity Launch and Dash suddenly disappeared. I could mouse over where it had disappeared and I could still interact with the invisible dash and launcher. I don't know why its doing this or how to fix it. Here's my system info:
Memory: 2.7 GB
Processor: AMD Athlon(tm) Processor TF-20 
Graphics: VESA: RS780MN
OS Type: 32 bit

Have you checked if unity2d is working?

You might just need a rest of unity.
crtl-f2 then
```
unity --reset
```Can be run in the 2d as well. 

Can be run in a terminal as well.

---

### Post by Frogbill on 2013-03-06
> **gamehero77 said:**
> I launched Eclipse on Ubuntu 12.04 and the Unity Launch and Dash suddenly disappeared. I could mouse over where it had disappeared and I could still interact with the invisible dash and launcher. I don't know why its doing this or how to fix it. Here's my system info:


I have the same problem with eclipse and sometimes this happents and when I start Chrome (not Cromium).
I really can't find what exactly is the problem, I will be gratefull if someone knows how to fix this.

Anyway, to bring back Unity use this:

```
sudo restart lightdm
```

P.S: Before you restart Unity, save your work because every running programme will be close.
Sorry for my bad English..

---


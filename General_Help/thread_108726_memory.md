---
title: "memory"
date: 2005-12-26
forum: General Help
---

### Post by tikal26 on 2005-12-26
hey I used to have 512 Meg of meory and upgraded to 2 gigs and now my meory gets eating up. I was just runig konqueror and a podcast in amarok and my memory got eaten up in like an hour. That can't be right than in an hour I would loose l two gigs of memory. Is there a way to fix this? maybe I set something wrong or maybe is an amarok problem I never listened to a podcast from amarok before.
Thanks for any suggestions

---

### Post by GoldBuggie on 2005-12-26
Please be more specific. Running top doesn't tell much other then how much memory is used. But linux uses almost all memory, that's how it is build. Run KinfoCenter and look at the memory there. Is the cache higher then the apps. data? If so don't worry that's how it should be. now if you have a huge amount of app data memory and no cache then I should start to worry.

---

### Post by alvonsius on 2005-12-26
How if my cache is smaller that application data? On KInfoCenter it shows 18% usage of cache and 78% app data, and at the current time I check, I got Quanta opened, MySQLCC, Konqueror,console,xCHM and Kontact plus the KInfoCenter itself. Is this okay? Or if not where can I set this memory stuf so it will become "well configured"??

PS: My physical memory is 512MB and swap is 290MB

---

### Post by tikal26 on 2005-12-27
I have 70% of my memory used and 38% cashed and I had konqueror, Amarok and firefox (rhapsody) and karamba opened. and an hour later I had 800 Megs of free memory and 400megs of cashed memory

Edit:
I started from scratch and at the beginning runnig from scratch with yakuake and karamba it only uses 100megs the problem was firefox and kontact specially kontact it was like eating my memory away. I just wished that rhapsody would support konqueror they already support safari so I don't think that it would be too hard.

---

### Post by GoldBuggie on 2005-12-27
Well I can't really specify a great solution for ya' I can only tell you that linux is basically designed to use all memory it gets. Some apps take up more memory then others. Firefox is known for beeing a memory-hog(baaad little fox) can't do much about it since it is in the code and often that's were most memory problems lie. In the code! I've seen some ppl having X taking up more then 6-10% and that is often a miss configuration with the xserver(xorg.conf). More then that I would say that if you don't feel that your system is getting slower and slower then don't worry about it. Only app I truly dislike that handles memory and cpu wrong/bad is bittornado(grrrrr).

If other solution then sit and do nothing is to recompile some basepackages and make them handle memory differently. This does not mean that they become better, only different.

So don't worry, be happy.

---


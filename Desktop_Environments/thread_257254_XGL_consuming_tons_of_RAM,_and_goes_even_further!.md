---
title: "XGL consuming tons of RAM, and goes even further!"
date: 2006-09-14
forum: Desktop Environments
---

### Post by turbojugend_gr on 2006-09-14
I know it is discussed already, yap I know using cgwd makes xgl consuming even more, but I haven't heard of this before: You see in my machine XGL start using about 130mb of ram. After I turn on kiba-dock and cairo-clock (i have a script for toggling them) it goes up to 150mb of memory, I use my machine as I would usually do and it can climb up to 600mb or even 700mb! It just keeps using more and more memory with no real reason, it climbs up 1 mb every 5mins for example (maybe less maybe more) and it never stops, in one case it even filled some of my swap memory space! Not to mention it literally "creeps" (very slOOoow perormance) when it clmbs above 500mb of memory usage. Also notice that both kiba-dock and cairo-clock stay at normal memory usage all-day long (10mb tops- never start climbing).

I know I maybe have to stop using cgwd, but I had 2gb memory (I was testing the one dim :( ) and so I hadn't any issues till the day before. The thing is that I don't get the memory usage growth effect, I definately think of it as a BUG, or misbehaviour, I can't understand why it needs more memory to perform the same tasks it does with only 200gb! 

Any help appreciated.

---

### Post by turbojugend_gr on 2006-09-14
Oh, I fogot, my specs are: 4400+ Athlon Dual Core
                           1GB DDR2 Ram (They took my other dim away- bloody bustards!)
                           nVidia 7800gtx Gpu

---

### Post by Dinerty on 2006-09-14
xgl/compiz is alhpha software and is very intensive and buggy:

Check this link for thread about it: [http://www.compiz.net/topic-3010-xgl-memory-consumption](http://www.compiz.net/topic-3010-xgl-memory-consumption)

When I open my Opera browser with a xgl sesion it uses about  150mb + memory, under normal gnome it is fine though heehee.

I usually do a restart once my ram usage hits 600mb, quite a few people have this problem :)

---

### Post by turbojugend_gr on 2006-09-14
Well to Dinerty and all other poor people having my Issue... A FIX IS OUT !!!

Yupeee! No more memory leeks! Quinstorm in his latest package (after a thorogh talk in a similar compiz-forums thread) made it! His last (0.69) version of cgwd fixes the memory leak issue, I am completely ok now! I suggest update for you all, it should apper in your update manager (if you are using Quinns repositories-which is the most usual case), but if does not appear you should "check for updates" in the update manager and the will bring up, no more memory leaks!

I 'll go thank Quinnstorm Admin in [this]("http://www.compiz.net/topic-3010-9.html") forums, all other having this problem should do that too, that guy seems to put a lot of hard work to make this sweet compiz rock, you rock major arse Quinn!

P.S.: Thanks dinherty for pointing the thread to me, I was disheartened all through the last page by the intensity of the phenomenon, but the last page was MANNA from the sky!

---

### Post by brucevangeorge on 2006-09-14
How does his XGL/Compiz work? Does it use the video ram to render the desktop as a series of textures?

Why does it use so much system ram? Special effect like warp, and woooble?

---

### Post by chavo on 2006-09-14
> **turbojugend_gr said:**
> Well to Dinerty and all other poor people having my Issue... A FIX IS OUT !!!

Yupeee! No more memory leeks! Quinstorm in his latest package (after a thorogh talk in a similar compiz-forums thread) made it! His last (0.69) version of cgwd fixes the memory leak issue, I am completely ok now! I suggest update for you all, it should apper in your update manager (if you are using Quinns repositories-which is the most usual case), but if does not appear you should "check for updates" in the update manager and the will bring up, no more memory leaks!

I 'll go thank Quinnstorm Admin in [this]("http://www.compiz.net/topic-3010-9.html") forums, all other having this problem should do that too, that guy seems to put a lot of hard work to make this sweet compiz rock, you rock major arse Quinn!

P.S.: Thanks dinherty for pointing the thread to me, I was disheartened all through the last page by the intensity of the phenomenon, but the last page was MANNA from the sky!

Yes Quinn is doing a fantastic job. There is one thing you should know though, Quinn is a woman.

---

### Post by turbojugend_gr on 2006-09-14
> Yes Quinn is doing a fantastic job. There is one thing you should know though, Quinn is a woman ...#-o

---


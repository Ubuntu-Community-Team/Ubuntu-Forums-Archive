---
title: "Dell XPS m15/1330 HDD load cycle issue"
date: 2008-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Clockswork on 2008-11-09
So I've seen alot of these HDD load cycle issues with the m1530 and the 1330. 

If you havent heard about the problem, if you listen closely you can hear the HDD click sometimes. Some people find it annoying but it can also be damaging if the HDD "clicks" to often.

So I have this problem along with alot of others and if you are just sitting with your laptop on a desk with no vibrations around you, you can easily apply the "ugly fix".

```
sudo hdparm -B 254 /dev/sda
```

This will cause the "needle" that is reading the HDD to stay on the HDD all the time and therefore never to jump or "click".

But this is not good to make permanent cause if you are on the go, lets say on a train where it is alot of bumps and vibrations. Forcing the needle to stay on your HDD all the time during these circumstances might make it scratch and damage your HDD. 

So I was wondering if there is a **proper** fix for this problem. And also, how damaging is it to just leave it as it is? (Let the HDD click)..
Is there maybe an ugly fix to apply when you are on the go? That stops te clicking but doesnt force the needle to be on the HDD all the time.

Thanks! :)

---


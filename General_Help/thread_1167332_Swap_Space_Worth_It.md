---
title: "Swap Space Worth It?"
date: 2009-05-22
forum: General Help
---

### Post by ALIENDUDE5300 on 2009-05-22
Hi, I want to know what you guys think about swap space... I have 3 gigs of RAM and a 750GB hard drive, so far I don't notice any problems without swap space, but would it be worth creating a swap partition, or would I rather just keep the free space? Is there much performance gain?

---

### Post by QIII on 2009-05-22
Although it is unlikely that you will really ever use up 3GB (except that there is a recently reopened bug in Xorg that can lead to a massive memory leak under certain circumstances), the Swap is used as "virtual memory" when you get close to using up your RAM.  Since that involves reading and writing to the disk, your performance will degrade somewhat.

But it's worthwhile to have some swap.

---

### Post by 73ckn797 on 2009-05-22
Keep the swap space. It is there for a reason.

---

### Post by TheNosh on 2009-05-22
i've never had any problems and i run with no swap space. that being said i would use swap if i hadn't already filled the four primary partition limit between /, /home, win 7 RC, and the "system reserve" from win 7

(and i know i could make a swap file, but i've been too lazy)

---

### Post by 73ckn797 on 2009-05-22
> **TheNosh said:**
> i've never had any problems and i run with no swap space. that being said i would use swap if i hadn't already filled the four primary partition limit between /, /home, win 7 RC, and the "system reserve" from win 7

(and i know i could make a swap file, but i've been too lazy)

I have run without a swap and encountered no problems. That was only for a brief period. I usually prefer swap to be on another drive whether using Ubuntu or Windows. That way the one drive is not getting too busy should swap be needed during any particular activity where swap is used.

---

### Post by dave31175 on 2009-05-26
> **QIII said:**
> Swap is used as "virtual memory" when you get close to using up your RAM I've been curious about this. I'm running 9.04 on a dinosaur with only 640MB RAM. Often the RAM is at 100% but the swap has never been used. It just fills up the RAM then runs more slowly :(

---

### Post by Cheesemill on 2009-05-26
If you want to be able to Hibernate your machine you need at least as much swap as RAM (not strictly true but close enough).

Cheesemill

---


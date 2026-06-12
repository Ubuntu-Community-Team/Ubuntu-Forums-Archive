---
title: "Need help with wireless"
date: 2010-09-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ry-no on 2010-09-29
My friend just did a fresh install on his Dell Mini Inspiron 10, just ubuntu only no XP or anything else.  When he clicks the wireless icon thing, wireless connections is in gray, and his hardware drivers did say Broadcom but now it says nothing.  How can he make connect and read wireless networks?

---

### Post by ry-no on 2010-09-29
Also, when i connect my ethernet cord to his laptop, it doesnt even connect to my internet at all.

---

### Post by Iowan on 2010-09-29
For the wired side:
If the ethernet card(s) is/are gigabit, a straight cable might work - otherwise, you'll need a crossover cable. 
Does your machine have Internet/Connection sharing set up?
From a terminal (Applications>Accessories>Terminal),
 check results of **ifconfig -a** Does the machine have an IP address?

Lest I forget... Welcome to the forums!

---

### Post by ry-no on 2010-09-29
it says inet addr: 127.0.0.1, is that it? like how will he connect wireless? confusing lol my ubuntu found my wireless connection right off the back

---


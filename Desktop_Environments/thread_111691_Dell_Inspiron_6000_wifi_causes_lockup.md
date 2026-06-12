---
title: "Dell Inspiron 6000 wifi causes lockup?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by bogl on 2006-01-02
After having taken an age to get wifi going at home on the Dell, I now find that any appreciable downloads seem to lock the machine up solid.  Not a problem with good old CAT-5.

dmesg reveals:

Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6

Is there an known issue with this driver?  Google does not reveal.

---

### Post by soulestream on 2006-01-02
I havent had that issue with mine. The 1.0.6 driver drops out more than I like, but I havent had it lock the machine up. 

Dell Inspirion 6000


Im going to try the 1.0.7 driver as soon as I get bored enough to install it

soule

---

### Post by Ginger The Cat on 2006-01-03
I think my  Inspiron 6000 wifi problems can be blamed on my wireless router which is a WAG54G Version 1. I can only get a reduced top speed out of the connection and the connection is only reliable if a second PC having a Linksys wireless card  is switched on at the same time. If my laptop alone is on it will lose the connection frequently. With the other PC on also the connection is rock solid.

Just saying this to suggest your problems might lie with your router?


Cheers

Mike

---

### Post by bogl on 2006-01-03
Thanks for the input folks.

My WAP is somewhat aged: a Netgear which only does 802.11b and is configured via Win-only tools.  Part of my problem was working out how to set it up correctly, as the documentation that came with it & on the Netgear website is laughable.  Once working, however, it seems to be fine.

Wifi works fine with the same laptop booted in XP Pro, which is what leads me to think it's a driver problem.

I think I will try upgrading the driver & associated - nice howto on the Kubuntu forums I spotted this morning.

Unless anyone else has any suggestions...

---


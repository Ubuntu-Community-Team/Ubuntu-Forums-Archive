---
title: "wireless not working on dell xps m1530"
date: 2010-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jboerum08 on 2010-07-09
I installed ubuntu 10.04 using wubi on my dell xps m1530 and when i boot ubuntu, the wireless icon wont come on unless i use the switch on the side of my laptop ( and i have to turn it on and off a few times till the wifi light stays on ) and when it does stay on i right click the network icon to enable wifi but i am not allowed to do so. One time i was able to enable it but unable to find any wireless network even though i was right 3 ft from a router. does anyone now how to help me!?!

---

### Post by workinhd on 2011-01-08
I think I figured out the pattern to get this working.  After booting up, slide the wifi switch to the off position.  Open terminal and run rfkill unblock all, may need sudo rfkill unblock all.  Then slide the wifi switch back to the on position.  This has worked for me, but I do have the Intel card.

---


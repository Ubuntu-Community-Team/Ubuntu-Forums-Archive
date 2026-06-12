---
title: "Inspirion 5100 Network Driver"
date: 2008-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DaveKong on 2008-05-27
I recently installed ubuntu(Hardy) on my Dell Inspiron 5100 which uses a Broadcom 4401 ethernet card. The card is supposed to be supported by the current 2.6.24 kernel but my network(wired) is not working. I tried manually configuring the connection which did not help anything. I even tried changing the kernel so it would not be modularized but included normally. I am quite confused and any information would be greatly appreciated.

I also tried the most recent xubuntu stable and debian stable installs and they failed as well.

---

### Post by OneShot on 2008-06-04
Similar Problem here ... I've got a DELL Inspirion 8600 and when I run the system from the Live CD the network does just fine, but once I'm finished with the install and reboot it wont work anymore. I've set all the stuff in the network manager (Static IP) just like before while running the live CD ... no joy.

Last night when I did the install for the first time everything worked after install till I did the first update run ... afterwards my network went out the window on the laptop.

Interesting, when I look at ifconfig I see that the eth0 only has a IPv6 adress and I have yet to find a way to add a IPv4 adress.

---

### Post by DaveKong on 2008-06-18
I just recently got my network (wired) to work. The seeming solution was to use a cat5e cable. This does not really make any sense but is supported by my empirical experimenting. I have no idea what is going on with it.

---


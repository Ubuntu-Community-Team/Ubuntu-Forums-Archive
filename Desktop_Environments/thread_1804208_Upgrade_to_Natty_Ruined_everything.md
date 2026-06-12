---
title: "Upgrade to Natty Ruined everything"
date: 2011-07-14
forum: Desktop Environments
---

### Post by jadacyrus on 2011-07-14
So, against my better judgement I did the upgrade to 11.04. And in typical ubuntu style it changed all my settings and broke everything. 

FIrst of all it put that Unity crap back on, which I specifically removed when I first installed ubuntu. Its useless and annoying.

SO i try t remove Unity / turn it off and now nothing works.

Secondly, it broke my compiz/emerald configuration so bad that compiz just seg faults now when I try to start it.

THirdly, I have no panels whatsoever. Only thing that shows is my desktop. If I can just get this thing back to normal , with our without compiz id be happy. 

Why does this have to happen every single time you upgrade? It's not worth the headaches anymore.

tl;dr:

Unity is broken, Compiz/Emerald seg faults, No panels, no window decorator. Pure ****

wtf?

---

### Post by wojox on 2011-07-14
Have you tried changing sessions at login and using "classic mode"?

---

### Post by jadacyrus on 2011-07-14
Switched to CLassic no effects and its back to nrormal now. THankgod, WIsh I knew about the sooner before messing around with everything.

THanks man. Im just going to pretend nothing happend now

---

### Post by Krytarik on 2011-07-14
If you want to try bring back Compiz with Emerald running:

The current package of Emerald included in the official repos of Natty 11.04 doesn't work with the current version of Compiz. So, try upgrading Emerald through this PPA:
[https://launchpad.net/~malteworld/+archive/compiz](https://launchpad.net/~malteworld/+archive/compiz)
```
sudo add-apt-repository ppa:malteworld/compiz
sudo apt-get update
sudo apt-get upgrade
```
Greetings.

---


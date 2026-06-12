---
title: "Which version of Ubuntu is better for gaming?"
date: 2009-06-11
forum: Gaming &amp; Leisure
---

### Post by alf717 on 2009-06-11
I wanted to try my hand at Ubuntu and have been working with the 9.04 AMD64 version for about two weeks now. I really want to game on Linux but I'm having an issue with Wine 1.0.1. and my ATI 3870 graphics card. I love playing CS 1.6 and my Steam install works great but when I run a game like Half-life or any mod they lock up my system for about two minutes until I eventually kill the processes in system monitor. Will I have better luck with an older version of Ubuntu? Or is it perhaps my version of WINE? Should I try a 32bit distro instead?

I've been watching a lot of videos on youtube of people that have great success with Ubuntu and WINE so I'm guessing I'm just doing something wrong.

My Setup:

AMD 5600+ 2.8Ghz
4GB of RAM DDR2-800
80GB Hard Drive
ATI 3870 (Catalyst 9.5 drivers)
Creative Audigy 2 ZS gamer edition

I was wondering if my sound card could be an issue as well. I'm using the default drivers since I could not find any drivers for my sound card.

---

### Post by x33a on 2009-06-11
try the latest version of wine:

1.1.23

---

### Post by alf717 on 2009-06-11
I tried Wine 1.1.23 but the results are the same. I also tried PlayonLinux and the trial of Crossover strangely got the same results. One other thing I'd like to note, when I run WINE (or any variant) they tend to run really slow and applications take a while to load. Went as far as removing everything from Synapse and reinstalled back to 1.0.1. Is it perhaps a driver issue? I can only run ATI 9.4 or ATI 9.5 drivers. When I try to install anything lowers the install fails. I'm curious if I'm missing something that should be installed.

---

### Post by Bölvaður on 2009-06-11
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507&iTestingId=40861](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507&iTestingId=40861)


look through the comments "at the bottom" of the page and see if you can gain anything from it. also google how to config counter strike to work with wine.
I didn't have to do any changes at all. config changes but wine is like a person.. it varies greatly between computers. you might need to change wine config AND half life config while another person might not have to do anything (or might already have done the changes for another game).

---

### Post by alf717 on 2009-06-12
Thanks for the help folks. I found stability using PlayonLinux and Ubuntu 8.10 AMD64 with Catalyst 9.3 drivers. Now my one and only issue is to solve why voice chat is locking up my system. For now it is off and I'm not really not missing much but I'm sure one of the WINE audio settings my help me out with this. Time to see if I can run my old Tomb Raider games. ;)

---


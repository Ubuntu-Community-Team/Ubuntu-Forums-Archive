---
title: "where can i get new repositories?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by lazcano on 2005-10-13
i got some problems with the breezy badger, first my aim messenger doesnt connect in msn server if i connect with my wireless card, second one i trying to find new repositories for breezy but i cant find it. :confused:

---

### Post by JavierPerez on 2005-10-13
I have the same problem... the repository is down... Is this normal?

---

### Post by aysiu on 2005-10-13
What do you mean by "new" repositories? What repositories do you have now?

---

### Post by majikstreet on 2005-10-13
[QUOTE=aysiu]What do you mean by "new" repositories? What repositories do you have now?[/QUOTE]
Like alternate repos i guess.....


They are experiencing a slashdot-like effect.

---

### Post by BLTicklemonster on 2005-10-13
slashdot.org has found out about Breezy, now every unemployed coffee shop bowzer and college know it all is ... ooh, that was mean! um, lot's of people who really want to kick their windows out are flooding in to get Ubuntu. The bandwidth is getting eaten up.

---

### Post by taurus on 2005-10-13
Good luck trying to connect to it because it's totally overload right now!!!  It takes forever to download something if you can get in...  I would wait for a day or so before I install something extra!  ;)

---

### Post by lazcano on 2005-10-13
I m sorry my bad, i am trying to say, where can i get extra repositories??? i mean universe and multiverse. 
and my another problem is my aim messenger, i cant get online, just with mi nic i can connect, with my wlan cant connect. but with mozilla i dont have any problems

---

### Post by invalid on 2005-10-13
Check to see that your sources.list looks like the following (which includes universe + multiuniverse)

[http://ubuntuguide.org/#upgradehoarytobreezy](http://ubuntuguide.org/#upgradehoarytobreezy)

Cheers,
Cb

---

### Post by mohuhau on 2005-10-13
open up /etc/apt/sources.list and replace all 
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) with 
[ftp://ftp.uninett.no/ubuntu](ftp://ftp.uninett.no/ubuntu)

This server got about 800-900mbit spare bandwith atm:) Its located in norway so if you outside of europe you could try another mirror. f.example:
[http://us.archibe.ubuntu.com/ubuntu](http://us.archibe.ubuntu.com/ubuntu) (change us with your country code or a country near you)

---


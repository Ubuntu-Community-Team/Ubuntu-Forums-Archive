---
title: "Java"
date: 2005-12-11
forum: General Help
---

### Post by JoshHendo on 2005-12-11
I can't seem to work out how to install java :P I tried followint the instructions on [http://ubuntuguide.org/](http://ubuntuguide.org/) , though that didn't seem to help. Anyone know a easy to follow way (hint, I like pictures :P). I searched the forum but nothing much. Any help appreciated :D

-Josh

---

### Post by M3ta7h3ad on 2005-12-11
If its the Java JDK your after I have it listed in aptitude.

apt-cache search JDK

and then just do

apt-get install whatever seems the most appropriate to you.

Thats all you need.

---

### Post by kaamos on 2005-12-11
Updating your sources: ```
sudo gedit /etc/apt/sources.list
```
Add the following line to the end of the file:
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
and run the command: ```
sudo apt-get update
```
Installing java jre or sdk:```
sudo apt-get install sun-j2re1.5
sudo apt-get install sun-j2sdk1.5
```

EDIT: Why use java from sun? It just works better..

---


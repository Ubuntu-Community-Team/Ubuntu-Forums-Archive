---
title: "Kde4 install not working on Ubuntu Gutsy"
date: 2008-01-24
forum: Desktop Environments
---

### Post by nickd63 on 2008-01-24
I have tried to install KDE following this procedure.

Adding deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to my /etc/apt/sources.list

Then, 
sudo apt-get update or
sudo aptitude update

Then, 

sudo apt-get install kde4-core
or
sudo aptitude install kde4-core

It fails the dependencies and stops.

Any suggestions?

---

### Post by jeffus_il on 2008-01-24
I think you need to remove the old KDE first, (aptitude remove) , I don't remember the exact package but it's on the forum or Google.

---

### Post by kellemes on 2008-01-24
Have you done this first?
*sudo apt-get remove kdelibs5 kde4base-data kde4libs-data*

---

### Post by nickd63 on 2008-01-25
Yes I have removed those pkgs

Have you done this first?
sudo apt-get remove kdelibs5 kde4base-data kde4libs-data

---


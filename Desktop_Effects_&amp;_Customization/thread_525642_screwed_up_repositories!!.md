---
title: "screwed up repositories!!"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by A-Sylum on 2007-08-14
i was installing compiz fusion and i added some things to my repositories to do this so anyway i was part way through installing compiz when i got an error and now my compiz is broken and i can't reinstall or remove it because i removed the repositories from where i got it. so.. Does anyone know how to fix this :D !!!!

---

### Post by andrewsomething on 2007-08-14
Could you post the errors that you get?

---

### Post by tgm4883 on 2007-08-14
re-put the repositories back into your sources.list?

---

### Post by A-Sylum on 2007-08-14
the problem is i cant find where i got the extra repos from so is there anyway to restore it to its original and force the computer to remove the software?


> The following packages have unmet dependencies:
  compiz: Depends: compiz-fusion-plugins-main (>= 0.0.0+git20070725) but it is not installable
          Depends: compiz-fusion-plugins-extra (>= 0.0.0+git20070725) but it is not installable
  compiz-core: Breaks: compiz-extra (<= 0.3.6.1-0ubuntu2) but 0.3.6.1-0ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
is what i get when i try to install aanything (i get the same with -f.)

---

### Post by tgm4883 on 2007-08-14
from here maybe 

[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

---

### Post by A-Sylum on 2007-08-14
well those were the same repositories i used. but i can't remove the packages or (preferably) reinstall them:
compiz
compiz-core

thanks :D

---

### Post by A-Sylum on 2007-08-14
Well i fixed it 

for anybody who wants to know it was because of broken files and bad repositories.

so here is the code i used

> 
sudo aptitude remove -f compiz


thanks for all your help :D !!!!

---

### Post by damansandhu on 2007-08-14
i get this error


Fetched 4B in 3s (1B/s)
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/multivers/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/multivers/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
daman@Ultimate:~$

---

### Post by A-Sylum on 2007-08-14
Note this will only help you if you are trying to get rid of a broken compiz!!!

> **damansandhu said:**
> i get this error


Fetched 4B in 3s (1B/s)
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/multivers/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/multivers/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
daman@Ultimate:~$

try opening up a terminal and typing in > gksudo nautilus

then go to etc/apt and open sources.list. replace the repositories you added for installation of the thing with
> deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse


then type in 
> sudo apt-get update

then type in
> sudo aptitude remove -f compiz
post back if there are any problems :D

NOTE: if the last line doesn't work try 
> 
sudo apt-get remove -f


---


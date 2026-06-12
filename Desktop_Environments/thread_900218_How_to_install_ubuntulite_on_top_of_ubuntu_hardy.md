---
title: "How to install ubuntulite on top of ubuntu hardy?"
date: 2008-08-25
forum: Desktop Environments
---

### Post by jittopjose on 2008-08-25
i have an installation of ubuntu hardy. i added lxde ppa and installed lxde. now i wish to try ubuntulite. is it possible to add ppa for ubuntulite and install it as did for lxde?. will it broke all my ubuntu existing system? i am not dare to try it out with out confirmation.
any idea about it?
thanks,
jittos....

---

### Post by kagashe on 2008-08-26
You need to remove the existing lxde installation completely including lxde ppa.

Add sources:
deb [http://ppa.launchpad.net/ubuntulite/ubuntu](http://ppa.launchpad.net/ubuntulite/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntulite/ubuntu](http://ppa.launchpad.net/ubuntulite/ubuntu) hardy main

sudo apt-get install Ubuntulite-desktop

kagashe

---

### Post by kagashe on 2008-08-26
Visited LXDE forum on freeforums and saw your post there as well.

If you visit [this page]("https://launchpad.net/~ubuntulite/+archive") you will know the difference between the two PPAs (mainly as follows)
* AlsaPlayer backported from Ubuntu's Developmental Branch
* GPicView backported from Ubuntu's Developmental Branch
* Kazehakase backported from Ubuntu's Developmental Branch
* PCManFM backported from Ubuntu's Developmental Branch
* ROXterm backported from Ubuntu's Developmental Branch
* WebKit backported from Ubuntu's Developmental Branch

kagashe

---

### Post by jittopjose on 2008-08-26
thanks for the replay,
in your opinion, which one would be better to use. ubuntu with lxde or ubuntulite?
i saw some of the builds in ubuntulite ppa is more newer than lxde ppa. thats why i thought of installing ubuntulite.
if i enabled ppa four ubuntulite, will it possible for me to select session on startup. it know its a stupid question, but i dont want to break my existing ubuntu installation... thats y am asking...
thanks,
jittos....

---

### Post by kagashe on 2008-08-26
> **jittopjose said:**
> thanks for the replay,
in your opinion, which one would be better to use. ubuntu with lxde or ubuntulite?
i saw some of the builds in ubuntulite ppa is more newer than lxde ppa. thats why i thought of installing ubuntulite.
if i enabled ppa four ubuntulite, will it possible for me to select session on startup. it know its a stupid question, but i dont want to break my existing ubuntu installation... thats y am asking...
thanks,
jittos....
To be frank Ubuntulite is still under development and if it breaks something you have nobody to blame. I am using lxde on Hardy but yet to try Ubuntulite so I have no personal experience.

I suggest you post your question on [Ubuntulite forum]("http://ubuntulite.tuxfamily.org/?q=forum").

kagashe

---

### Post by jittopjose on 2008-08-27
i asked this in ubuntulite forum. they told, we can install ubuntulite after removing all the lxde components as well as the source list entry. otherwise there would be some conflicts. after installing ubuntulite, we can select it by changing session to LXDE. this wouldn't affect total system
thanks,
jittos....

---


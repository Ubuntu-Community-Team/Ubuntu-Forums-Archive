---
title: "MATE 1.2 Installation problems"
date: 2012-04-30
forum: Desktop Environments
---

### Post by GaryIKILLYOU on 2012-04-30
Hi, so I'm having some problems installing MATE 1.2 into 12.04 after I've made the move to 12.04. I've tried to install MATE in both a 32 and 64 bit environment and still am having no luck. 
I've tried using the installation guides on the net, and not a one of them has worked at all. 
I add the repo, but when I do the update, it gives me 404 errors for the MATE repo. 
I'd really like to jump to 12.04, but I don't like the DE at all and would like to get MATE installed.

---

### Post by Frogs Hair on 2012-04-30
Hello and Welcome

That may be temporary and the is not much you can until you can connect with the sever. Some PPAS for mate have no packages packages built for 12.04 so track the instructions you are using to launchpad and make sure they are up to date. Information and instructions on blogs can be outdated or wrong.

---

### Post by GaryIKILLYOU on 2012-04-30
> **Frogs Hair said:**
> Hello and Welcome

That may be temporary and the is not much you can until you can connect with the sever. Some PPAS for mate have no packages packages built for 12.04 so track the instructions you are using to launchpad and make sure they are up to date. Information and instructions on blogs can be outdated or wrong.

Thank you for the quick reply. I am using the instructions from the original website. 
[http://mate-desktop.org/install/#ubuntu](http://mate-desktop.org/install/#ubuntu)
They also have a forum, but no place to inquire help. Otherwise I would have done it there. 
I guess I will wait a couple of days and try again. I'll just have to use xfce or use the gnome shell. 
Thanks anyways.

---

### Post by merlinus on 2012-04-30
I managed to install Mate, but almost nothing worked as it should.  It also loaded tons of extra libraries and apps.

Frankly, Gnome Classic in 12.04 looks and works better.  YMMV.

---

### Post by opiumpoetry on 2012-05-01
Yesterday I installed MATE using the instructions [here]("http://www.noobslab.com/2012/04/install-mint-mate-12-on-ubuntu-1204.html") and it works fine on my Ubuntu 12.04 Toshiba laptop. Here they are for pasting into your Terminal in case you have trouble opening the webpage for any reason:

*sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) $(lsb_release -cs) main"
*sudo apt-get update
*sudo apt-get install mate-archive-keyring
*sudo apt-get update
*sudo apt-get install mate-desktop-environment

---


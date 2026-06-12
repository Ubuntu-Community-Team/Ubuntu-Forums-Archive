---
title: "how to install compiz fusion on fiesty fawn?"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by ishanmahajan on 2007-12-02
hi 
im a newbie to linux and have ubuntu 7.04 and have installed beryl on it. I love the visual effects but now i want to install compiz fusion. can anyone help me with its installation and do I have to remove beryl first?
Thankyou

---

### Post by macaholic on 2007-12-02
I would remove beryl completly first, then the best way, IMO, is to use amaranth's repositories.
Open up a terminal, type ```
gksudo gedit /etc/apt/sources.list
``` When that window opens up, add these lines to the bottom, ```
 deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
```
After that run ```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
```
After, assuming everything installed nicely, you can run compiz with, ```
compiz --replace
``` You can configure it by running ```
ccsm
```
or by System > Preferences > CompizConfig Settings Manager

---


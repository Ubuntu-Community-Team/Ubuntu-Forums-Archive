---
title: "No FIre Effect Compiz"
date: 2009-05-29
forum: Desktop Environments
---

### Post by Reyes1986 on 2009-05-29
When I've installed Compiz Fusion in the past, fire effect was already there (in animations) this time it's not listed, how can I get it to be listed?

Thanks

---

### Post by LinuxRules1 on 2009-05-29
You have to enable the Animations Add-On.

[ATTACH]115557[/ATTACH]

---

### Post by Reyes1986 on 2009-05-29
Okay, here's the weird part, its not listed...

---

### Post by Reyes1986 on 2009-05-29
> **Nate8nate said:**
> I just made it with git.

Here's how


Open Terminal and enter
```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
``````
mkdir ~/compizplugins
``````
cd ~/compizplugins
``````
git clone git://anongit.compiz-fusion.org/fusion/plugins/animationaddon
``````
cd animationaddon
``````
make
``````
BUILD_GLOBAL=true sudo make install
```It should now show up in CCSM.

Got it now thanks

---

### Post by Sand &amp; Mercury on 2009-05-29
Erm, just running *sudo apt-get install compiz-fusion-plugins-extra* would've sufficed.

---


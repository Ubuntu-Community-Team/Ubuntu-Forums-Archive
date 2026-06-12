---
title: "missing animation addon plugin in compiz"
date: 2009-06-30
forum: Desktop Environments
---

### Post by haterforever on 2009-06-30
hey ubuntu ppl, i'm using compiz and initially had the animationaddon option but now it is no longer available, any idea on how to get it back

---

### Post by gettinoriginal on 2009-06-30
Are you saying it is missing from CompizConfig Settings Manager ??  (see screenshot)[ATTACH]119468[/ATTACH]
If it is missing, then just reinstall it via Synaptic or Terminal.

---

### Post by haterforever on 2009-06-30
yeah that's missing, i tried removing and reinstallin all compiz components  via synaptic manager but no luck. do u kno which component deals with that addon?

---

### Post by gettinoriginal on 2009-06-30
Here are the ones that I have, not sure which one is for the animations.
[ATTACH]119469[/ATTACH]

---

### Post by haterforever on 2009-06-30
installed everythin u had but still not gettin the option.thanks for the pic though

---

### Post by gettinoriginal on 2009-06-30
Just on a whim, go back to synaptic and tic each one for "reinstall".

---

### Post by contactpraveen2001 on 2009-07-17
Try this it works for me ..

Open Terminal and enter
Code:

sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

Code:

mkdir ~/compizplugins

Code:

cd ~/compizplugins

Code:

git clone git://anongit.compiz-fusion.org/fusion/plugins/animationaddon

Code:

cd animationaddon

Code:

make

Code:

BUILD_GLOBAL=true sudo make install

It should now show up in CCSM.

[http://ubuntuforums.org/showthread.php?t=1118379&page=2](http://ubuntuforums.org/showthread.php?t=1118379&page=2)

---


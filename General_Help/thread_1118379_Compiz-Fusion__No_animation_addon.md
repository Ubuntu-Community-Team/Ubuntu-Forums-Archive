---
title: "Compiz-Fusion:  No animation addon"
date: 2009-04-06
forum: General Help
---

### Post by Nate8nate on 2009-04-06
I have updated to 9.04 from 8.10 and after the update the plug-in Animation Addon is gone.


See attachment.


FIXED

> I just made it with git.

Here's how


Open Terminal and enter

```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```

```
mkdir ~/compizplugins
```

```
cd ~/compizplugins
```

```
git clone git://anongit.compiz-fusion.org/fusion/plugins/animationaddon
```

```
cd animationaddon
```

```
make
```

```
BUILD_GLOBAL=true sudo make install
```

It should now show up in CCSM.

---

### Post by linuxuser21 on 2009-04-06
No it's not.  It's the second one in effects.

---

### Post by Nate8nate on 2009-04-06
That only has the basic ones, not the fire, paper airplane, beam up and some other ones.

---

### Post by linuxuser21 on 2009-04-06
Check this out: [http://ubuntuforums.org/showthread.php?t=969032](http://ubuntuforums.org/showthread.php?t=969032) that has some solutions.

---

### Post by Nate8nate on 2009-04-06
I've read that already.  I don't have animation addon in the list of disabled plug-ins.

---

### Post by Lunx on 2009-04-06
Always worth installing the unsupported plugins if you want some extra features (note: They mention that these plugins may be problematic on some systems, but seem to run fine on my low/average spec machine)

```
sudo apt-get install compiz-fusion-plugins-unsupported
```

---

### Post by linuxuser21 on 2009-04-06
Okay.  Did you look in the Synaptic Package Manager?  You should have compiz-fusion-plugins-extra installed.

---

### Post by linuxuser21 on 2009-04-06
> **Lunx said:**
> Always worth installing the unsupported plugins if you want some extra features (note: They mention that these plugins may be problematic on some systems, but seem to run fine on my low/average spec machine)

```
sudo apt-get install compiz-fusion-plugins-unsupported
```

+1
I think this one might have it too.

---

### Post by Nate8nate on 2009-04-07
I have those installed.

---

### Post by Lunx on 2009-04-07
Well I have no idea why you haven't got the animation plugin. Only thing I can suggest is mark Compiz for a re-install and see if that solves it. What release of Ubuntu you using?

---

### Post by chriskin on 2009-04-07
i have the same problem too, even though i have all packages compiz-related installed

---

### Post by Nate8nate on 2009-04-07
Reinstalling didn't help...

---

### Post by chriskin on 2009-04-07
> **Nate8nate said:**
> Reinstalling didn't help...

didn't work for me either :S

---

### Post by chriskin on 2009-04-07
> Major change is Animation plugin restructuring, there are still some rough edges like compiz crashing if animation addon is enabled, so please do not use the packages on production system, only for the developers and testers to report and fix bugs.


taken from a compiz-fusion related blog
let's just wait

---

### Post by Nate8nate on 2009-04-07
I just made it with git.

Here's how


Open Terminal and enter
```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```
```
mkdir ~/compizplugins
```
```
cd ~/compizplugins
```
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/animationaddon
```
```
cd animationaddon
```
```
make
```
```
BUILD_GLOBAL=true sudo make install
```

It should now show up in CCSM.

---

### Post by chriskin on 2009-04-07
> **Nate8nate said:**
> I just made it with git.

Here's how


Open Terminal and enter
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/animationaddon
``````
cd animationaddon
``````
make
``````
BUILD_GLOBAL=true sudo make install
```It should now show up in CCSM.


is it stable? as i said before, compiz developers call it unstable 

please give us feedback :)
i'll most probably try it tomorrow but i would really like to know beforehand :)

---

### Post by Nate8nate on 2009-04-07
The last update on the animationaddon plug-in was 5 months ago, and it seems to be quite stable.

---

### Post by chriskin on 2009-04-07
> **Nate8nate said:**
> The last update on the animationaddon plug-in was 5 months ago, and it seems to be quite stable.

then it's a positive, i will install it first thing tomorrow

thank you for the links, i searched a bit but found only a dead link on some half-dead forum :P

LET'S SEE SOME FIRE ON THE DESKTOP :)

---

### Post by Genserowski on 2009-04-27
FIXED => thx man! It works great.

"Group and Tab Windows" disappeared, too. Have you got any ideas?

---

### Post by contactpraveen2001 on 2009-07-17
> **Nate8nate said:**
> I just made it with git.

Here's how


Open Terminal and enter
```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```
```
mkdir ~/compizplugins
```
```
cd ~/compizplugins
```
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/animationaddon
```
```
cd animationaddon
```
```
make
```
```
BUILD_GLOBAL=true sudo make install
```

It should now show up in CCSM.
thx man ...it works ...

---

### Post by mkarthik90 on 2010-06-05
I am not having the animations such as air plane , beam up and burn.  what should be done to get those animation effects in the compiz config  settings?

---


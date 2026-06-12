---
title: "Awn"
date: 2008-03-05
forum: Desktop Environments
---

### Post by chaos315 on 2008-03-05
Hey -- I installed awn and had no applets, so i uninstalled and reinstalled a different build "awn-bzr" -- now it is completely gone -- the forums say it takes a while, and to restart, but I have done that and still nothing - i can get into the settings and see everything - tons of applets and all, but no awn on my desktop - I have compiz-fusion on - and the 3D is working fine (I did the glx gears) is there another setting in compiz that I need to enable or something stupid that I haven't thought of?

---

### Post by notwen on 2008-03-05
Not sure which howto you tried, but try [this one]("http://ubuntuforums.org/showthread.php?t=572019").  It will install the latest AWN along w/ some additional applets.

Depending on how you installed it your previous attempts you will need to remove all related pacakges through Synaptic or change into the source's directory and run these commands in term:

```
sudo make uninstall
sudo rm -f /usr/local/bin/awn-manager
sudo rm -f /usr/local/bin/avant-*
```

Then proceed w/ the howto linked above.  It also has some instructions to help you remove any previous instructions at the very start of it.  Simple copy & pasting is involved.  Post back or on that thread should you run into any problems.  =]

---

### Post by chaos315 on 2008-03-14
thx

---


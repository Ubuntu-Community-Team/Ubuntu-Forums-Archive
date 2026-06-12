---
title: "Fightcade main.py not running"
date: 2015-05-10
forum: Gaming &amp; Leisure
---

### Post by nep-nori on 2015-05-10
So yeah, big time fan of old school 2D fighters here, which is what made me download Fightcade to give it a spin. This video:[ http://www.youtube.com/watch?v=ZSsQmJEvkO0]("http://www.youtube.com/watch?v=ZSsQmJEvkO0") was very helpful, but then when I double-click on main.py nothing happens. Also, if I go to the terminal and type ```
sudo python main.py
``` while in the Fightcade folder I get the following error: ```
Traceback (most recent call last):
  File "main.py", line 9, in <module>
    import sip
ImportError: No module named sip
``` could you guys and gals help me out? surely it's just me missing a package or something...

---

### Post by R33D3M33R on 2015-05-10
There is a install file in the package: linux-install.sh that you should run before trying to play. It executes this:

```
sudo apt-get install wine python-qt4-phonon python-qt4
```

---

### Post by nep-nori on 2015-05-10
Thank you R33D3M3R, that was a quick fix :) and just in case anyone runs into the same bump I did and is sent here via google: ```
sudo bash linux-install.sh
``` while in the FightCade folder.

Thread marked as solved.

---


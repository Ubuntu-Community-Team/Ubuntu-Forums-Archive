---
title: "FrozenPUZZLE"
date: 2008-06-17
forum: Gaming &amp; Leisure
---

### Post by BanskuZ on 2008-06-17
[img]http://img90.imageshack.us/img90/742/frozenpuzzleve2.png[/img]

Simple puzzlegame (no, it's not tetris) where you try to get "blockgroups". Blockgroups must contain four blocks (at minimum) and they all must share the same color.

Download (and doubleclick colors.py): [http://up.servut.us/dl/8830](http://up.servut.us/dl/8830)
If not working, install python+pygame:
```
sudo apt-get install python python-pygame
```

If you are having performance issues, blame Python and SDL for not having proper hardware acceleration, and create a file named 'conf.ini':
```
kx=475
ky=480
solve=0
bggfx=0
effects=0
helpergfx=0
```

---


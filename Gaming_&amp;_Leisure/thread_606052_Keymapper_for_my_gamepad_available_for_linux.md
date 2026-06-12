---
title: "Keymapper for my gamepad available for linux?"
date: 2007-11-07
forum: Gaming &amp; Leisure
---

### Post by Nick Blinko on 2007-11-07
Right now I can't afford a desk to put my computer on (I have it sitting on a piece of plywood on top a cinder block) It's really uncomfortable to try and plays games on my pc hunched over, so I setup my xbox controller for use in linux. Some of my games support joysticks natively, but not fully. For example, soldier of fortune only supports 4 of the 12 buttons available, and only one analog stick. Also, not all of my games support joysticks either. 

So is there any program out there that'll let me map keyboard keys to my gamepad and/or allow my analog stick to function as a mouse? I'd really appreciate it, it's so much of a pain the *** to play games as of now.

---

### Post by mbradlcu on 2007-11-12
you may want to check out 'xev', from there find out what the system is seeing when you press the buttons/stick controller. If you do see input then I suspect you could map it with in the game.. hope it helps,,

---

### Post by Ferrat on 2007-11-14
Im guessing your running your Xbox gamepad via USB, I've made a keymap that applys (attached)

as for programs 

JoyToKey works great in wine for games running under wine but not for Linux natvie games.

QJoyPad works the sameway as JoyToKey and under linux but when I tried it, it ate CPU like crazy, using 50-90% of if even in idle mode (could be a settings problem)
EDIT!! : Found a french site where they fixed the 100% CPU drain that was ecause it checked madly for all actions 
with a deb and all =)
[http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100](http://www.azriek.fr/index.php?post/2007/10/07/qjoypad-ubuntu-gutsy-et-occupation-CPU-a-100)


RejoysTick is another but haven't tried that one yet

Joy2key is another as well and in the repos

there are lots of programs out there =)

---


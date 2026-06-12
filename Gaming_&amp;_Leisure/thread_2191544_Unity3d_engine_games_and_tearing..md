---
title: "Unity3d engine games and tearing."
date: 2013-12-03
forum: Gaming &amp; Leisure
---

### Post by pnarciso on 2013-12-03
Every single game that uses unity3d engine suffers from tearing even with vsync turned on. The engine detects that a compositor is used and it shutsdown vsync automatically. Is there any way to avoid this. I'm running ubuntu 13.10 by the way.

---

### Post by dannyboy79 on 2013-12-03
stop using a compositor. compositing software will just make your CPU and GPU suffer anyway when if you want to game, you don't need the compositing effects anyway so i'd suggest turning them off when gaming. not sure otherwise

---

### Post by pnarciso on 2013-12-03
If Ubuntu Unity is a plugin of compiz, which is a compositor, it's impossible to switch off the compositor. Compiz itself was supposed to switch off when fullscreen applications are running but it's not always the case.
The only workaround I have found was to install openbox, and switch to it when I want to run those games. But that's a dirty solution. Windows don't suffer from this issues, so Ubuntu devs must do something about it, if they want to promote it as a serious gaming OS.

---

### Post by dannyboy79 on 2013-12-03
at your greeter you would choose Unity 2D instead of normal Ubuntu desktop (can't you do that?) I don't believe Ubuntu is marketing their OS as a serious gaming OS and it's not even Ubuntu's fault, it's really the graphics card manufacturers not releasing drivers that are on par with windows drivers or at least adiquete documentation about their hardware so the open source drivers can be improved.

i also wouldn't call the openbox solution a dirty solution, running the most minimal desktop manager while you want to game is the best idea because you want all your computers resources to go towards the game. this is just my opinion and you'r entitled to your own. :)

---

### Post by pnarciso on 2013-12-06
Submitted the bug at [https://bugs.launchpad.net/unity/+bug/1257382](https://bugs.launchpad.net/unity/+bug/1257382)
I've also posted some unity3d engine game demos for trying.

---


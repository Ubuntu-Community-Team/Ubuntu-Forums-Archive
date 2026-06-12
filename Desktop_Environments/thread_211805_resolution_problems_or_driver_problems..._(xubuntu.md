---
title: "resolution problems or driver problems... (xubuntu)"
date: 2006-07-08
forum: Desktop Environments
---

### Post by darkcow on 2006-07-08
well, i downloaded and I burned xubuntu and installed it on my old toshiba tecra 8000 laptop. well, it installed nicely and its running ridiculosly fast for this old OLD laptop. but one problem. i cant get any high resolution (i need 1024x768). all it will let me is something is 320x240 or default.


any solutions or config files i need to change?


-darkcow

---

### Post by CombatGod on 2006-07-21
Hmm... I'm having the same problem... I don't know what it is. If I find something out I'll let you know.

---

### Post by nalmeth on 2006-07-21
Open a terminal and type:
sudo dpkg-reconfigure xserver-xorg

Pick defaults for everything, unless you know better, and when you get to resolutions, add the ones you need.

---

### Post by CombatGod on 2006-07-21
sudo dpkg-reconfigure xserver-xorg

Try that.

---


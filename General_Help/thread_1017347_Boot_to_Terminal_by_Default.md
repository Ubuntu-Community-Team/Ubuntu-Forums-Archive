---
title: "Boot to Terminal by Default"
date: 2008-12-21
forum: General Help
---

### Post by thenocturnalhoodie on 2008-12-21
Hey guys, I was wondering where I could change the setting to have my computer boot to the ubuntu terminal by default, instead of my gui. 

(running 8.04 if you needed to know)
tuXfiles says that setting is located in /etc/inittab
but it doesn't seem to exist in my computer...
I'm assuming that they must be using a different distro.

---

### Post by bodhi.zazen on 2008-12-21
just disable or rename gdm

sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/s30.gdm

You can then either use startx or any other window manager or if you want a gdm

sudo /etc/init.d/gdm start

---


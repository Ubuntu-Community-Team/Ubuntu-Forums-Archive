---
title: "how to uninstall completely compiz"
date: 2011-04-05
forum: Desktop Environments
---

### Post by tybo42 on 2011-04-05
Hello,

I want to uninstall compiz but I have some problems. When I completely remove the package with Synaptics, compiz is still installed on my computer! Few days ago I installed compiz following this website ([http://wiki.compiz.org/Installation/Stable](http://wiki.compiz.org/Installation/Stable) for 8.6), and it probably explains why. Now how do I revert the process? How do uninstall everything? I tried sudo apt-get remove compiz* but it tells me the it cannot locate compiz-check (even though it is installed).

Help much appreciated.

T.

---

### Post by 3Miro on 2011-04-05
You did not install compiz from Synaptic or the Software Center, hence you cannot use those to remove it. You should go to the terminal, then cd into the folder where you compiled compiz (where you typed "make" and "make install") and then type
```
make uninstall
```
and/or
```
make clean
```

Make sure compiz is gone, if so, you can then delete the folder.

---

### Post by tybo42 on 2011-04-06
Great, thanks! Solved!

---


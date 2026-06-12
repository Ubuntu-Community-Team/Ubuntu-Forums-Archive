---
title: "apt-get install realplayer problem"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Matthai on 2006-07-14
apt-get install realplayer - there is dependeny problem.

realplayer depends from xlibs, but this package is broken.

Who to inform to fix this?

---

### Post by Titus A Duxass on 2006-07-14
The best way to install realplayer is to use automatic.  Apt-get often has problems with dependencies, try using aptitude instead.

As for reporting the problem, I don't think you can.

---

### Post by jordilin on 2006-07-14
I wouldn't install realplayer from apt-get. If I remember the dependency is sth like lib5stdc++. In any case if you only want to install the latest realplayer go to [www.real.com/linux](www.real.com/linux) download the player and do:
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
accept/answer all the questions and that's all.

---

### Post by Matthai on 2006-07-14
OK, solution: apt-get install realplay

---


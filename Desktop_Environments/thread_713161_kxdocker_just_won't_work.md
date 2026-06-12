---
title: "kxdocker just won't work"
date: 2008-03-02
forum: Desktop Environments
---

### Post by Guardian-Mage on 2008-03-02
Ok, right now I hate kxdocker so much I don't want to write about it, but I need a replacement for Stardock Objectdock. I have tried the .deb 0.33 and it didn't work, then I tried to compile it from scratch using 1.04. I even used this command:

./configure --prefix=`kde-config --prefix`

Right now I have it installed by compiling it using 
sudo su
./configure --prefix=`kde-config --prefix`
make
make install

When I start it I get all these errors about missing files. When I tried the above without sudo I asked me for the configuration file.

How do I install it?

---

### Post by ayoli on 2008-03-02
kxdocker is no longer maintained (and also requires patch to work with composite environment (eg : compiz)).
The kxdocker's devs have launched a new project [xqde]("http://xqde.xiaprojects.com/"), you may want to check it.

---


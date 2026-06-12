---
title: "Cannot retrieve Mixxx from the repos :("
date: 2009-02-19
forum: General Help
---

### Post by cespinal on 2009-02-19
Hey to all!, 

Im trying to download mixxx from the repos but it seems the package is not available. 

is it any way I can report this? and also, is it anyway to get it from other source rather than compiling it? cuz I really don't know anything about compiling from source. 

thanks :D

---

### Post by taurus on 2009-02-19
There is a version for Ubuntu so why not download that, .deb, and then click it to install.

[http://www.mixxx.org/download.php](http://www.mixxx.org/download.php)

---

### Post by cespinal on 2009-02-19
just dont know how I didnt see it. 

okay, downloaded the package, but i cannot run it, heres de error: 

dependency is not satisfiable: libjack0.80.0-0

why is this?

---

### Post by taurus on 2009-02-19
It's because mixxx needs that library.  So if you don't have it installed on your machine, you need to install it first before you can install mixxx.

You can install it either from add/remove or synaptic.  You can also install it from a terminal.

```
sudo apt-get update
sudo apt-get install libjack0
```

---

### Post by cespinal on 2009-02-19
done... now I stumbled upon another wall :P 

error this time: dependency is not satisfiable: lib qt4-opengl

---

### Post by taurus on 2009-02-19
Why don't you open up synaptic and search for that package, libqt4-opengl.  Install it from there.  

Or install it from a terminal if you wish.

---

### Post by cespinal on 2009-02-19
/i have them already :( .....dazzling

---

### Post by cespinal on 2009-02-19
im trying to install the .deb package in ubuntu hardy - mint 5. but im encountering an error:

dependency is not satisfiable libqt4-opengl

 okay. I begun getting all the packages needed but here's what happens:

I try to intstall libqt4-opengl, but it conflicts with libqt4-gui.

If I remove libqt4-gui, it will take libqt4-qt3support out with it.

I decide to go on and do it. Then I at last, install libqt4-opengl

Back to mixxx, but I now get it needs libqt4-qt3support!!! which at the same time installs with openqt4-gui, conflicting again with libqt4-opengl!!

hahaha WHAT THE......

---


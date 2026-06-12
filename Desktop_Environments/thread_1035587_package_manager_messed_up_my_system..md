---
title: "package manager messed up my system."
date: 2009-01-09
forum: Desktop Environments
---

### Post by hockey97 on 2009-01-09
Hi, I just recently installed some new updates and after it installed the stuff I got a list of stuff that was uninstalled.

So now I have missing files for alot of things. I can't run the ubuntu package manager.

Now ubuntu gives me a window for .deb packages that it's not a supported format.

what should I do??

---

### Post by taurus on 2009-01-09
You mean synaptic?  Run it from a terminal and see what happens.

Applications -> Accessories -> Terminal
```
gksudo synaptic
```

---

### Post by hockey97 on 2009-01-09
ok,I get this from what you said to type in the terminal. 

here it is: :/# gksudo synaptic
The program 'gksudo' is currently not installed.  You can install it by typing:
apt-get install gksu


it seems it uninstalled itself weird... I will do that apt-get command.

---

### Post by taurus on 2009-01-09
Are you running intrepid, 8.10?  If you don't have gksu/gksudo on your system anymore, that could explain why synaptic won't run from System -> Administration -> Synaptic Package Manager.  You need to reinstall gksu again.

```
sudo apt-get update
sudo apt-get install gksu
gksudo synaptic
```

---


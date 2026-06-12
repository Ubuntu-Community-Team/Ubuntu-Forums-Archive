---
title: "compiz animation (burn/beam/airplaine)"
date: 2009-07-15
forum: Desktop Environments
---

### Post by AhPook on 2009-07-15
I do no have more additional animation on compiz...
this is a screenshot of my compiz packages on synaptic...
sorry for my bad english, i'm italian 
[[IMG]http://img148.imageshack.us/img148/4866/schermatau.th.png[/IMG]]("http://img148.imageshack.us/i/schermatau.png/")

---

### Post by Toadinator on 2009-07-15
I have the same problem. Everything worked fine in 8.10 before I upgraded.

---

### Post by AhPook on 2009-07-16
> **Toadinator said:**
> I have the same problem. Everything worked fine in 8.10 before I upgraded.

i resolved with

1 delete repository of compiz from sources.list 
2 uninstall compiz and compiz-core with -sudo apt-get --purge remove *****
3 uninstall with synaptic all packages compiz
4 delete hide folder .compiz in home and folder compiz in hide folder .config in my home
5 removed the orphaned libraries with - gtkOrphan
6 restart session o restart pc
7 install from synaptic compiz   compiz-core and plugins/compiz...

---


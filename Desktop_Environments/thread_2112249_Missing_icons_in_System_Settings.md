---
title: "Missing icons in System Settings"
date: 2013-02-04
forum: Desktop Environments
---

### Post by ubunet on 2013-02-04
Hi,

I use Ubuntu 12.10 (Unity) and "Appearance" icon is missing in "System Settings". I included the "Date" icon installing the *indicator-datetime* service.

I don't know why is missing! I need Appearance to change the size of icons.

---

### Post by Frogs Hair on 2013-02-04
Hello and Welcome

Try the following and log out and back in. ```
sudo apt-get install --reinstall gnome-control-center 
```

---

### Post by JohnMac on 2013-07-10
I had exactly the same bug.

From Launchpad Questions:

Go to System Settings/Appearance then change the Theme and then change it back.

Worked for me !

System:

Desktop 
AMD 5200 x2 Processor
1.9Gb RAM
Ubuntu 12.04

---


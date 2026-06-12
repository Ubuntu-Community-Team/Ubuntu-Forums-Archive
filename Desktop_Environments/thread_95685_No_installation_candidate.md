---
title: "No installation candidate"
date: 2005-11-27
forum: Desktop Environments
---

### Post by CharlieC on 2005-11-27
Hi;
I am trying to work with Ubuntu 5.10. I notice when I try to install some applications I get the message there is "no installatin candidate". Let me guess these are in some way propriatory.
The the three specifically are Azureus, w32codecs and libdvdcss. 
I am brand new to Ubuntu and pretty new to linux in general. 
I suppose I could go to the Azureus site and download it from there. 
I have googled for the other packages and there are lots of results. I guess the question is do I add a web site to the repositories or something like that, assuming I can find one?
If I have to install them seperately, I dont know what path they need to be in.
Please let me know if this is correct and if now where am I going wrong.

TIA
Charlie

---

### Post by dafl00 on 2005-11-27
```
apt-cache search [whatever you're looking for] 
```
if you're using the command line.. 

click on System > Administration > Synaptic for the GUI version

---

### Post by Perfect Storm on 2005-11-27
You need to set up your repo to get non-gpl stuff:

[http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

---


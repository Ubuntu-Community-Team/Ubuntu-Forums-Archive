---
title: "Installation of xfce4.10 Xubuntu 12.04"
date: 2012-05-14
forum: Desktop Environments
---

### Post by rinainverse on 2012-05-14
Xubuntu12.04 is installed in mac mini of powerpc g4 loading and used. 

[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)

This site was seen and upgrade to xfce4.10 was tried. 

Synaptic Package Manager is opened and it is "Mark all upgrades". 
A "Apply" button cannot be pushed although the button was pushed. 

If it carries out, how can xfce be updated to 4.10?

---

### Post by 2F4U on 2012-05-14
If you read through the comments section of the link you posted you notice that there are serveral problems with this ppa. So, unless you are willing and able to fix them, I would suggest that you stay on what comes with 12.04.

---

### Post by rinainverse on 2012-05-14
Please teach me the installation method from a source code.

---

### Post by dekker on 2012-05-14
i've installed 4.10 from the following link, but tbh it doesnt make much difference, i wont be upgrading my 2 other machines.

[http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html](http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html)

the link has been updated since it was first posted.

---

### Post by rinainverse on 2012-05-14
Synaptic will ask to remove one package and install a new one?

---

### Post by rinainverse on 2012-05-14
It tried on the information on the following link places again. 

[http://www.therightguy.info/2012/05/12/xfce4-10-official-ppa-for-ubuntu-12-04/](http://www.therightguy.info/2012/05/12/xfce4-10-official-ppa-for-ubuntu-12-04/)

When the following commands were executed, the error occurred. 

sudo apt-get install xfce4

How can an error be lost if it carries out? 

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xfce4 : Depends: xfwm4 (>= 4.10.0) but 4.8.3-1ubuntu1 is to be installed
         Depends: xfconf (>= 4.10.0) but 4.8.1-1 is to be installed
         Depends: xfce4-settings (>= 4.10.0) but 4.8.3-1ubuntu3 is to be installed
         Depends: xfce4-panel (>= 4.10.0) but 4.8.6-2ubuntu2 is to be installed
         Depends: xfdesktop4 (>= 4.10.0) but 4.8.3-2ubuntu7 is to be installed
         Depends: thunar (>= 1.4.0) but 1.2.3-3ubuntu2 is to be installed
         Depends: gtk2-engines-xfce (>= 3.0.0) but it is not going to be installed
         Depends: xfce4-session (>= 4.10.0) but 4.8.3-0ubuntu2 is to be installed
         Depends: xfce4-appfinder (>= 4.10.0) but 4.8.0-3 is to be installed
         Recommends: desktop-base (>= 5.0.4) but it is not going to be installed
         Recommends: thunar-volman (>= 0.8.0) but 0.6.1-0ubuntu1 is to be installed
         Recommends: tango-icon-theme (>= 0.8.90) but it is not going to be installed

E:Unable to correct problem, you hove held broken packages.

---

### Post by rai4shu2 on 2012-05-14
> **rinainverse said:**
> Xubuntu12.04 is installed in mac mini of powerpc g4 loading and used.

The PPA only has x86 and x86-64 versions. You need to build a PowerPC version if you want to run Xfce 4.10 on your system. You should know:

* 4.10 still has some reported problems (see elsewhere on this forum)
* You will have to build from source which is a little tedious.

If you do build from source, you should first thoroughly read this guide:

[http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building)

---

### Post by dentaku65 on 2012-05-14
You can do it in this way

```
sudo apt-get install ppa-purge
```
```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
```
```
sudo apt-get update
```

**If you already have Xubuntu installed**
```
sudo apt-get dist-upgrade
```
```
sudo apt-get remove xfce4-session && sudo apt-get update && sudo apt-get dist-upgrade
```
**If you don't have Xubuntu installed**
```
sudo apt-get install xubuntu-desktop
```

If you want to remove the Xfce 4.10
```
sudo ppa-purge ppa:xubuntu-dev/xfce-4.10
```

by

---

### Post by rinainverse on 2012-05-14
> **rai4shu2 said:**
> The PPA only has x86 and x86-64 versions. You need to build a PowerPC version if you want to run Xfce 4.10 on your system. You should know:

* 4.10 still has some reported problems (see elsewhere on this forum)
* You will have to build from source which is a little tedious.

If you do build from source, you should first thoroughly read this guide:

[http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building)

The contents are unclear although explanation of the link place was read. 
Would you teach concrete compile order?

---

### Post by rinainverse on 2012-05-14
building of xfce4.10 -- teaching the method. 
Please let me know order for the command to execute later on.

---

### Post by rai4shu2 on 2012-05-14
The wording is somewhat technical, but the order is very explicitly stated:

> The Xfce packages need to be built in a specific order. If you don't follow this, compile options might not be available or the configure stage will abort because of missing dependencies.

Read the guide and follow it. It's really as simple as that. If you have a particular question about a step involved, feel free to ask in this thread. :)

---


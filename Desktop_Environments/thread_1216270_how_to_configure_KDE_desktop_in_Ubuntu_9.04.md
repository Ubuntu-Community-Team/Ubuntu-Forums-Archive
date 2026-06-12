---
title: "how to configure KDE desktop in Ubuntu 9.04"
date: 2009-07-18
forum: Desktop Environments
---

### Post by ahmadonly on 2009-07-18
Hi friends, 

i'm a new user on Linux and Ubuntu. I have just installed  Ubuntu 9.04 on my system and i want to know how to install or configure KDE 4.2 Destop on my system.

---

### Post by ibutho on 2009-07-18
Hi and welcome to the forum.

Did you install Ubuntu or Kubuntu? Ubuntu comes only with GNOME, so if you want KDE, you will have to install kubuntu-desktop using the packaging tools e.g. Synaptic or from the CLI
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
To log into KDE, just choose it from the Session list in the login manager.

---

### Post by vinutux on 2009-07-18
> **ahmadonly said:**
> Hi friends, 

i'm a new user on Linux and Ubuntu. I have just installed  Ubuntu 9.04 on my system and i want to know how to install or configure KDE 4.2 Destop on my system.

Add repo to your system

**[COLOR="DarkOliveGreen"]deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) jaunty main[/COLOR]**

if you don't know how

open software sources System>Administration>software sources 
.. in third party software tab add this line **deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) jaunty main **

reload an upadate.....:D

---

### Post by ahmadonly on 2009-07-18
thanx ibutho for your kind held, yes i'm using ubuntu, and your guidence has helped me. now i'm installing it.......

---

### Post by vinutux on 2009-07-18
> **ibutho said:**
> Hi and welcome to the forum.

Did you install Ubuntu or Kubuntu? Ubuntu comes only with GNOME, so if you want KDE, you will have to install kubuntu-desktop using the packaging tools e.g. Synaptic or from the CLI
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
To log into KDE, just choose it from the Session list in the login manager.

He want KDE 4.2 ...

---


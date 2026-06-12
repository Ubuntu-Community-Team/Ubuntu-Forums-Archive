---
title: "thinking of switching to Kubuntu"
date: 2007-05-14
forum: Desktop Environments
---

### Post by Korrontean on 2007-05-14
Hi there.

I'm a very happy Ubuntu 6.06 user. It works perfectly fine on my computer. However, I look at my workmate's Kubuntu and I have to admit it looks much better. I am afraid of Kubuntu running a little slow on my computer. What do you think?

Acer Aspire 3500
*Celeron 1.5 ghz Intel® Celeron® M
*1 GB RAM DDR333

---

### Post by vtel57 on 2007-05-14
Ubuntu and Kubuntu are the same operating system. They just use different desktop managers... Gnome or KDE. You don't have to reinstall the entire system again. Just install the KDE desktop environment and use it as you default desktop manager.

---

### Post by Korrontean on 2007-05-14
:oops: :oops: :oops: 
Well, just when I thought I knew SOMETHING about Ubuntu I discover I am an, ehem, ignorant.
I guess it was kind of confusing to see Ubuntu and Kubuntu in differente distribution CDs.
THANKS!

---

### Post by vtel57 on 2007-05-14
You're welcome. KDE is in your Ubuntu repos. You can install it with Synaptic and then set it as default with Sessions Options in the login screen. By the way, you have ample resources to run KDE.

Luck!

---

### Post by qpieus on 2007-05-14
I think KDE would run just fine on your pc. See this link for more info on installing kubuntu desktop on your pc: [http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

typing in a terminal:
```
sudo apt-get install kubuntu-desktop
```
will install it for you.

---

### Post by Nythain on 2007-05-14
kubuntu is my flavor of choice, and it topped with beryl flies just fine on my p4 2.0ghz with only 768megs of ram... its not as bloated and resource instensive as some would have one believe, though granted its not xfce or fluxbox...

---

### Post by aysiu on 2007-05-14
> **qpieus said:**
> I think KDE would run just fine on your pc. See this link for more info on installing kubuntu desktop on your pc: [http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

typing in a terminal:
```
sudo apt-get install kubuntu-desktop
```
will install it for you.
Just try it out and see. If you don't like it, uninstall it.

---

### Post by vtel57 on 2007-05-15
I used to be a hard core Gnomie, but I've been learning KDE in some of the other distros I have on my system. It is an outstanding desktop manager. What turned me off about it initially was that I was learning Linux and Gnome at the same time. I just didn't have the cerebral space at that time to deal with learning KDE too. Since that time, though, I've begun to use KDE extensively. I also still use Gnome in some of my distros. It's the best of both worlds. Next up? XFCE. ;)

---

### Post by icefaerie on 2007-05-15
It's better to install it with *sudo aptitude install kubuntu-desktop*, rather than apt-get.  That way, if you don't like KDE, you can completely remove KDE and all of the associated libraries and programs with a simple *sudo aptitude remove kubuntu-desktop*.  apt-get does not keep track of dependencies like aptitude does.

---


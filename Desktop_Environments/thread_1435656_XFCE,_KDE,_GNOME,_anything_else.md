---
title: "XFCE, KDE, GNOME, anything else"
date: 2010-03-21
forum: Desktop Environments
---

### Post by oleink on 2010-03-21
Hey is it possible to get xfce, kde and gnome with the same ubuntu distro and select them in "session" before logging on?  Can I run xfce sometimes and ubuntu gnome others?

---

### Post by soltanis on 2010-03-21
Yes you can. I think the appropriate packages are

ubuntu-desktop = gnome
kubuntu-desktop = kde
xubuntu-desktop = xfce

From gdm, the login manager, you can select which one you want to use when logging in.

---

### Post by oleink on 2010-03-21
How do I install them like with the terminal and will my computer continue to run the same speed?  (I like how much faster ubuntu is than other operating systems)

---

### Post by soltanis on 2010-03-21
```

sudo apt-get install ubuntu-desktop kubuntu-desktop xubuntu-desktop

```

In general installing packages you just put the package name after sudo apt-get install.

You can search package lists using

```

sudo aptitude search <keyword>

```

Installing all three desktop environments will use much more disk space (since all of them will install their own apps) and I don't know how much they will interfere with each other (KDE and Gnome have competing Network Managers and similar programs that tend to like to enable themselves in each other's environments).

Generally speaking, since you only run one session at a time when you log in, the performance impact should be minimal.

---

### Post by oleink on 2010-03-21
alright I may just get XFCE than.  Thanks! also if i decided to get rid of it would that be possible too?

---

### Post by oleink on 2010-03-21
Got Xfce now too!

---

### Post by n0dix on 2010-03-21
Please, @oleink don't post multiples threads with the same issue. 
[http://ubuntuforums.org/showthread.php?t=1435611]("http://ubuntuforums.org/showthread.php?t=1435611")

---

### Post by oleink on 2010-03-22
Sorry.  I was told to move my thread here because the other post was in beginner stuff.  (still new to the forums)

---

### Post by 3Miro on 2010-03-22
> **oleink said:**
> Hey is it possible to get xfce, kde and gnome with the same ubuntu distro and select them in "session" before logging on?  Can I run xfce sometimes and ubuntu gnome others?

I have all three and I switch between them depending on my mood.

I installed Ubuntu with Gnome first, then
```
sudo apt-get install kubuntu-desktop
sudo apt-get install xfce4
```

You probably want xfce4-goodies as well (I am not sure what xubuntu-desktop would install, maybe a few extras).

---

### Post by oleink on 2010-03-22
Is LXDE any good? What are its primary uses?

---

### Post by sixdrift on 2010-03-22
LXDE is a really good desktop. Its fast and efficient. It uses fewer resources than GNOME, KDE, and xfce. I have been running it for a couple of seeks now doing some tests.

---

### Post by oleink on 2010-03-22
Thanks for the reply.  I got my laptop for free besides the hard drive.  The former owners had fried theirs.  I am going to upgrade to 4gb of ram but I want to be able to run this computer as smoothly as possible

---


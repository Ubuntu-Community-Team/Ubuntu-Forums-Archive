---
title: "Which desktop environment should I use?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by LostArt on 2007-05-05
Currently I have the regular old ubuntu, but now I'm curious as  to which Desktop environment I should use, KDE, Gnome, Gentoo, etc,etc... Which one is the best, If I change to a different type will I lose all my data.

By best I kinda mean, which one can I customize the most to suit my needs, I can't run beryl, but I would like transparent windowsand other effects

---

### Post by taurus on 2007-05-05
Ubuntu uses Gnome and Gentoo is just another Linux distro, not a window manager.  If you want to run KDE, just install it and check it out yourself.

```
sudo aptitude 
sudo aptitude install kubuntu-desktop
-or-
sudo aptitude install xubuntu-desktop  <-- for XFce4
```

---

### Post by LostArt on 2007-05-05
> **taurus said:**
> Ubuntu uses Gnome and Gentoo is just another Linux distro, not a window manager.  If you want to run KDE, just install it and check it out yourself.

```
sudo aptitude 
sudo aptitude install kubuntu-desktop
-or-
sudo aptitude install xubuntu-desktop  <-- for XFce4
```

Oh, well how is Gentoo, what is it like compared to Ubuntu?

---

### Post by taurus on 2007-05-05
For a newbie or somebody who doesn't have time or care much about how it operates, you should stick with Ubuntu because it's simple.  If you want to build every package there is for your machine, then you can try Gentoo.  It would take hours (or even days) to get it up and running the way you want.

---

### Post by LostArt on 2007-05-06
Allright, so I'll use gentoo later in life

---

### Post by Uodnelome on 2007-05-06
I have heard that installing Ubuntu first and then KDE on top of it is a better route to go than going for Kubuntu first.  (For various reasons, something about administrative tools -- I actually don't know the validity of this suggestion.)

However, I'm interested in using some of the KDE-specific programs like KOffice, but wouldn't need the redundancy of GNOME Office alongside it.  For someone coming from a lifelong use of Windows (until this year with limited experience with Debian GNU/Linux in a computer lab), would that much of a hassle?

---

### Post by Nythain on 2007-05-06
wich desktop you should use is entirely up to you... i like kde, others hate it. if your machine is older, xfce might be right for you... its lightweight, and decently customizable.

the easiest way to give them all a try would be the above mention of sudo apt-get install (insertflavorhere)-desktop

once you find one you like, i would highly recommend downloading the distro of ubuntu for it, and then just installing any other extra apps you might want/need.

I install kubuntu then from there add things like firefox and synaptic wich doesnt come with it by default... while others will install ubuntu and just add apps like amarok wich doesnt come standard in ubuntu

---

### Post by LostArt on 2007-05-06
Well, I installed KDE, but it won't work, do I have to do something else, All I did was run this command

sudo aptitude install kubuntu-desktop

---

### Post by jfinkels on 2007-05-06
> **LostArt said:**
> Well, I installed KDE, but it won't work, do I have to do something else, All I did was run this command

sudo aptitude install kubuntu-desktop

Next time you log in (before you log in, more accurately), change the "Session" to "KDE" instead of the Default Session (GNOME).

---

### Post by LostArt on 2007-05-06
Yeah, I did that It won't start, It just says 

could not start kstartupconfig. check your instalation

What do I have to do ugh

---

### Post by LostArt on 2007-05-06
err, how do I uninstall it, then I could try reinstalling it? I guess

---

### Post by Rui Pais on 2007-05-07
you can reinstall with:
```
sudo aptitude reinstall kubuntu-desktop
```

or remove with:
```
sudo aptitude remove kubuntu-desktop
```



Try to xfce4:
```
sudo aptitude install xubuntu-desktop 
```

or fluxbox:
```
sudo aptitude install fluxbox
``` 
(that is very light but you can use anything you miss from, gnome or xfce4 if you keep both.

Another, a complete DE but harder (and in a lot of ways better) is e17:
[http://ubuntuforums.org/showthread.php?t=319336](http://ubuntuforums.org/showthread.php?t=319336)

good luck

---

### Post by EXCiD3 on 2007-05-07
When i first started using Linux i only used GNOME, I heard alot about KDE and decided to try it out. After getting used to GNOME, KDE was a very sleek interface yet I could not find the settings near as easily as I could in GNOME and have since then decided on Ubuntu w/KDE installed later (my installation of Kubuntu w/GNOME didnt work quite right). I hardly evar use KDE anymore. Gnome seems to be much more of a newbie friendly environment ;)

---


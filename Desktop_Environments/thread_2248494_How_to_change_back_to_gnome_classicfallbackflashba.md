---
title: "How to change back to gnome classic/fallback/flashback desktop in Ubuntu 12.04"
date: 2014-10-15
forum: Desktop Environments
---

### Post by tlotr on 2014-10-15
Hi All,

I wanted to know how to change back to gnome classic desktop in Ubuntu 12.04.

I have tried sudo apt-get install gnome-session-fallback --> Doesn't work
sudo apt-get install gnome-session-flashback --> Doesn't work.

```
ubuntu@ubuntu:~$ sudo apt-get install gnome-session-fallback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-session-fallback is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-session-fallback' has no installation candidate
ubuntu@ubuntu:~$ 

```

```
ubuntu@ubuntu:~$ sudo apt-get install gnome-session-flashback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-session-flashback
ubuntu@ubuntu:~$ 

```

How can I go back to the gnome classic desktop. The one which shows Application, Places on top and there is a panel at the bottom too where it shows the softwares that are open/active and also shows the 4 Desktops.

---

### Post by kc1di on 2014-10-15
Hi tlotr,
```
gnome-session-fallback 
``` is the right code. 
Check to make sure that the universe repository is enabled.

You may at this point  be better off installing the mate desktop instead of fallback.
you can find how to do that on [this page. ]("http://www.webupd8.org/2014/03/how-to-install-mate-18-in-ubuntu.html")
Mate is a fork of Gnome 2 and has exactly what your asking for. 
good Luck :)

---

### Post by oldfred on 2014-10-15
Some packages are just references to others.
I also have seen this 

sudo apt-get install gnome-panel

       Precise Gnome Classic Tweaks and Tricks - Cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
From this thread by kansasnoob
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
But fallback discontinured but rename flashback very similar
[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

---

### Post by oldrocker99 on 2014-10-15
The classic GNOME 2.x we all miss so much has been resurrected as MATE, which is now my go-to desktop. Here's how to install it for 12.04:
```
sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --no-install-recommends ubuntu-mate-core ubuntu-mate-desktop
```

Try it! You may like it!

---

### Post by ibjsb4 on 2014-10-15
> --no-install-recommends ubuntu-mate-core ubuntu-mate-desktop
I have a stand alone session of Fallback.  Going to give this a try just to see if they will play nice :)

---


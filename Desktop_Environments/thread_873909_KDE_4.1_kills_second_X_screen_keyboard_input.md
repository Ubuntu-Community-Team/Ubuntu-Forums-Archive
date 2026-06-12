---
title: "KDE 4.1 kills second X screen keyboard input"
date: 2008-07-29
forum: Desktop Environments
---

### Post by syyid on 2008-07-29
Hi
I just upgraded to KDE4.1 (was using KDE4.0). My setup includes 
Twinview with 2 screens and a third screen run as a separate X Server (No Xinerama)
Anyways I usually start up krdc on the third screen via commandline
(krdc --display :0.1 but after the upgrade , any thing I type is echoed onto the command line it was launched from instead of the screen / application. 
Additionally for some reason KWallet popped up on the same screen (separate X /3rd) and had the same issue I couldn't type anything into it at all.
Any ideas?

---

### Post by SunnyRabbiera on 2008-07-29
KDE 4 has been nothing but a pain in my opinion, thats why I still use KDE 3 or Gnome.

---

### Post by syyid on 2008-07-29
Heh I just switched back to KDE3.x to test it out and its working correctly over there (as expected). One thing that I hadn't noticed before 
KDE3 - Second screen has its own taskbar / startup menu etc
KDE4 and KDE4.1 - Second screen is a black void - any way to fix that?

---

### Post by syyid on 2008-08-10
Made slight progress, its now functional. I noticed the second screen had no decorators, running kwin on the second screen allowed me to type into it.
DISPLAY=:0.1 /usr/lib/kde4/bin/kwin

Still haven't been able to get a menu or taskbar to display on the second screen.

---

### Post by Corn Flake on 2010-07-01
> **syyid said:**
> Made slight progress, its now functional. I noticed the second screen had no decorators, running kwin on the second screen allowed me to type into it.
DISPLAY=:0.1 /usr/lib/kde4/bin/kwin

Still haven't been able to get a menu or taskbar to display on the second screen.

As of Kubuntu 10.04 Lucid, the above still works.  I was having the same problem with mythtv and huludesktop.  I now just use
```
DISPLAY=":0.1" kwin &
```
and then run the program and everything works as it should.

---


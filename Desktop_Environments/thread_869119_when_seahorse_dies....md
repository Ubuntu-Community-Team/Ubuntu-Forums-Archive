---
title: "when seahorse dies... ?"
date: 2008-07-24
forum: Desktop Environments
---

### Post by renauldo on 2008-07-24
seahorse has proven very unreliable for me.  When it dies, is there any way to get desktop-wide ssh-agent functionality back (without running a new instance and setting it up in every single terminal I might want to use)?

If there isn't a way to do this, are there some instructions laying around somewhere for configuring to use plain old ssh-agent and purging seahorse from my system?

Logging in / out of my desktop to get seahorse going again is awful.  My workflow requires ssh access to dozens of different boxes at times in dozens of different terminals.  Restarting all that everytime seahorse dies is a serious enough PITA that I'm tempted to just switch to OSX (egads).

---

### Post by Potatoj316 on 2008-07-24
Umm I dont really know what your problem is.  If you want an ssh client open a terminal and type ```
ssh USER@IP
```
to remove seahorse this should work
```
sudo aptitude remove seahorse
```

---

### Post by renauldo on 2008-07-28
> **Potatoj316 said:**
> Umm I dont really know what your problem is.  If you want an ssh client open a terminal and type ```
ssh USER@IP
```
to remove seahorse this should work
```
sudo aptitude remove seahorse
```

ssh USER@IP doesn't automatically login if the ssh-agent is dead or unknown, and typing in my password 300 times for dsh ops is really not feasible.

Just wanted to know if there was someway to restart seahorse after it dies and have its setting take effect globally on my desktop.  I.e., get your seahorse going, check that it works, then kill it and see if gnometerms (or whatever you use) can be made to know about a new seahorse instance that you start up (without exporting SSH_ env vars separately in each term).

---

### Post by pkkid on 2009-05-12
I just hit this thread from Google and wanted to post that removing seahorse, will also have the side effect of removing ubuntu-desktop.  If you remove it, your system may become unstable.. and according the the details of ubunut-desktop, upgrades will no longer work.

---

### Post by ElijahLynn on 2012-08-23
Happens to me all the time too. Subscribing for a fix.

---

### Post by coffeecat on 2012-08-23
Old thread - closed.

---


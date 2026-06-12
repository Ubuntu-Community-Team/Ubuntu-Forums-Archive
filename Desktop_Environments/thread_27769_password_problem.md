---
title: "password problem"
date: 2005-04-17
forum: Desktop Environments
---

### Post by dthsqd on 2005-04-17
I got a bit of a problem...

I installed Kubuntu and was able to set my username and a password, however, I don't know how to log on to root.

I set a password, but whenever I try to log into the Root Terminal, I type in my password and its incorrect.  I can't install anything :-x so I'm in a bit of a standstill.

---

### Post by dthsqd on 2005-04-17
Ah nevermind, I forgot that you manually configure the UNIX password yourself.

---

### Post by ludi on 2005-04-17
[QUOTE=dthsqd]I got a bit of a problem...

I installed Kubuntu and was able to set my username and a password, however, I don't know how to log on to root.

I set a password, but whenever I try to log into the Root Terminal, I type in my password and its incorrect.  I can't install anything :-x so I'm in a bit of a standstill.[/QUOTE]

Use YOUR password when some app ask or sudo. You can enable the root login in kdm or gdm. 
In KDM:
/etc/kde3/kdm/kdmrc
(change this line to true) AllowRootLogin=false
You can disable this function but whatever...
Before, make a sudo passwd root and set your root password.

---


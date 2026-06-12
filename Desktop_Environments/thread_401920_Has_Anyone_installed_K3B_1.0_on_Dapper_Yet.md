---
title: "Has Anyone installed K3B 1.0 on Dapper Yet?"
date: 2007-04-05
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-04-05
I keep getting dependancy errors for Kdelibs42Ca and LibksB2, theyre already installed!
Ive had these errors before, its some kind of Dapper only Lib or something, has anyone got a fix for it?
Steve

---

### Post by Storm Rider on 2007-04-05
This isn't exactly what your asking but I have K3B 1.0 running fine on Edgy.  Didn't have to do anything special.

---

### Post by mister_p_1998 on 2007-04-05
Well I tried installing on my Edgy machine at work, and got the same errors!
Steve:lolflag:

---

### Post by ZipoTe on 2007-04-05
did you follow this? ---> [http://k3b.plainblack.com/installation]("http://k3b.plainblack.com/installation") i did and everiyhig was ok :D

First, I recommend you this:
- open a terminal and type: sudo apt-get install build-dep k3b, to get everything you need

then follow the guide ^^

---

### Post by lagartoflojo on 2007-04-09
I have the same problem you do:
```
$ sudo apt-get install k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.5-0ubuntu3.3 is to be installed
       Depends: libk3b2 (>= 1.0~3v1ubuntu0) but 0.12.17-1ubuntu3 is to be installed
E: Broken packages
```
As you can see, we need version 4:3.5.5-1 of kdelibs4c2a but only version 4:3.5.5-0 is available in the reps. Similar problem for libk3b2.
In the official ubuntu reps, only k3b 0.12.17 is available. Why is apt-get/Synaptic trying to upgrade to k3b 1.0? Because I have treviño's repository ([http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/3v1n0) in my sources.list... unfortunately, the required versions of the kde libs are not in that rep.
So the question is, where do we get them?

---

### Post by mister_p_1998 on 2007-04-10
OK I got it working on Edgy.. dont think youre going to want to go through all this though...
installed KDEBase
QT v3.2 & V4
FULL install of KDE
it took TWO hours to ./configure on a 1.1MHZ Duron
It still gives an error on startup that it cant find K3B MAD MP3 decoder or VCD encoders
But it looks really nice and copies & burns OK.
Steve

---


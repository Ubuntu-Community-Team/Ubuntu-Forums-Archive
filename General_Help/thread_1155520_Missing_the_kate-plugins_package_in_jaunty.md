---
title: "Missing the kate-plugins package in jaunty"
date: 2009-05-10
forum: General Help
---

### Post by monsterstack on 2009-05-10
I can't seem to find the "kate-plugins" package in Jaunty. Also, there aren't any plugins in the version of Kate I have installed. Am I missing a repository or two? Here's the relevant stuff from my sources.list if that's the case:
```

deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted 
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe 
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe 
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://getswiftfox.com/builds/debian unstable non-free
deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/vperetokin/gnote/ubuntu jaunty main #gnote

```

---

### Post by ashmew2 on 2009-05-13
Hi,
Which version of kate are you using ? 

Paste the output of :
```

kate --v
```

---

### Post by monsterstack on 2009-05-13
Thanks for getting back to me.

```

Qt: 4.5.0
KDE: 4.2.2 (KDE 4.2.2)
Kate: 3.2.2

```

---

### Post by ashmew2 on 2009-05-13
Ill be glad if you get it sorted out :)

Btw , are you running Kubuntu or Ubuntu Jaunty ? If its Ubuntu , what do you need Kate for ? Gedit ftw! :P

Okay , so i searched around for a bit and i found this : 
[https://bugs.launchpad.net/ubuntu/+source/kdeaddons/+bug/289624](https://bugs.launchpad.net/ubuntu/+source/kdeaddons/+bug/289624)

It's a reported bug that the kate-plugins cannot be installed on Jaunty/Intrepid.

So i guess leaving it as it is until its fixed would be a good idea..

If you still want , i think you *should be able* to get the kate-plugins from one of hardy's repositories but then you might have broken dependencies..It's not recommended as well , but ok...Add this line to your /etc/apt/sources.list :

deb [http://mirror.mcs.anl.gov/pub/ubuntu hardy main]("http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/k/kdeaddons/kate-plugins_3.5.9-0ubuntu1_i386.deb")
```

do a sudo apt-get update
```then try : 
```

sudo aptitude install kate-plugins
```
It might work but then again there's a fair deal of risks involved..

---

### Post by monsterstack on 2009-05-13
> **ashmew2 said:**
> Ill be glad if you get it sorted out :)

Btw , are you running Kubuntu or Ubuntu Jaunty ? If its Ubuntu , what do you need Kate for ? Gedit ftw! :P

Okay , so i searched around for a bit and i found this : 
[https://bugs.launchpad.net/ubuntu/+source/kdeaddons/+bug/289624](https://bugs.launchpad.net/ubuntu/+source/kdeaddons/+bug/289624)

It's a reported bug that the kate-plugins cannot be installed on Jaunty/Intrepid.

So i guess leaving it as it is until its fixed would be a good idea..

If you still want , i think you *should be able* to get the kate-plugins from one of hardy's repositories but then you might have broken dependencies..It's not recommended as well , but ok...Add this line to your /etc/apt/sources.list :

deb [http://mirror.mcs.anl.gov/pub/ubuntu hardy main]("http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/k/kdeaddons/kate-plugins_3.5.9-0ubuntu1_i386.deb")
```

do a sudo apt-get update
```then try : 
```

sudo aptitude install kate-plugins
```
It might work but then again there's a fair deal of risks involved..

Thanks for googling that for me. I guess I really should have dugg deeper into it. I use regular ol Jaunty, but I have most of the KDE stuff installed too. I like Gedit, although my main workhorse is Geany.

I've mixed repositories before, when I ran Debian. It was not a good time to be me. I think I'll just wait for the fix. Thanks for your help :)

---

### Post by ashmew2 on 2009-05-14
I hope they release the fixes soon! :D

---

### Post by rosencrantz on 2011-11-09
To whom it may concern: kate-plugins is now a part of kate. Selected plugins can be activated via Settings->Configure Kate..

---

### Post by oldos2er on 2011-11-09
Closed, please don't bump old threads.

---


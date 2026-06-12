---
title: "Upgrading to KDE 4.5 RC wrecked my Ubuntu"
date: 2010-07-05
forum: Desktop Environments
---

### Post by sleepitoff on 2010-07-05
I'm looking for help here before I resort to reinstalling Ubuntu. So last night I installed KDE 4.5 via ppa:kubuntu-ppa/beta and after the upgrade I only get a black screen and mouse cursor at login. Anybody might have any ideas or tricks to get this working again, or even resort back?

---

### Post by lkjoel on 2010-07-05
You can downgrade via synaptic.
Also, you should NEVER add beta core components to your system (unless you are trying to fix problems with the beta version).

---

### Post by Zorael on 2010-07-05
Make sure you have **plasma-desktop** installed.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade plasma-desktop+
```

---

### Post by sleepitoff on 2010-07-05
Thanks, Zorael. I ran that in recovery mode and it was what I needed

---


---
title: "On-screen keyboard sucks; can it be fixed?"
date: 2019-06-30
forum: Desktop Environments
---

### Post by DrPotoroo on 2019-06-30
I've kind of posed a question on this before, but before it was just about the log-in screen, now it has now become more general. Ubuntu 16.04, which I was using previously, had a pretty okay on-screen keyboard: in that I could access every key I needed. Now, on ubuntu 19.04, there seems to be no way to access keys like ctrl, esc, etc. There is loads of screen real-estate just being wasted when the on-screen keyboard comes up where these keys could be put ... why aren't they there? One of the saving graces on linux of having to deal with an on-screen keyboard are those great shortcuts that can save laborious typing - shortcuts like tab completion (nope! - no tab key in the on-screen keyboard!); ctrl+r (nope! - no ctrol key available!) ... Why in the world would anyone create a keyboard that has emoji but NOT ALL THE BASIC KEYS A KEYBOARD HAS? Please, somebody tell me there is some tweak somewhere that gives me all the standard keyboard keys - or that I'm an idiot and I've just missed seeing that really obvious button that reveals all the keys.

---

### Post by Autodave on 2019-06-30
I would try a live version of 18.04 and see if all the keys are there.  I am assuming that you upgraded from 16.04.  If you did, upgrading often times creates problems just like what you are having.  If the live version works, you may want to do a clean install of 18.04.

---

### Post by DrPotoroo on 2019-07-06
Not an upgrade. This is a brand new computer with a clean install of 19.04. It really looks like this is the design of the gnome 3 onscreen keyboard, and that the design is just really, really poorly thought out.

---

### Post by uRock on 2019-07-06
It doesn't look like 18.04 has that ability, either.

---

### Post by #&amp;thj^% on 2019-07-06
See if this is installed;
```
apt policy onboard
```
If not try it, it might be worth the while.
To change settings use:
```
onboard-settings
```

---


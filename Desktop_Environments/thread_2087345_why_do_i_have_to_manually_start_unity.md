---
title: "why do i have to manually start unity?"
date: 2012-11-23
forum: Desktop Environments
---

### Post by pc10pc on 2012-11-23
I'm having problems with unity. when i log in i have to CTRL+ALT+T to bring up terminal and start unity, as it doesn't load otherwise. I've left it for a few minutes to see if it was slow loading, but nothing happened.
other user account loads it no problem.
started happening when i was messing around trying to get unity webapps to work, so more than likely my fault!worked no problem after installing.
im on 12.10.

---

### Post by stinkeye on 2012-11-23
Try setting compiz/unity to default settings with
```
dconf reset -f /org/compiz/
```
...then logout/in

---

### Post by 2F4U on 2012-11-23
Is this a fresh install or an upgrade? Do you have the problems from the beginning? If it works for other users, it is likely that some settings for this particular user are the problem.
You can try 

unity --reset

in a terminal.

---

### Post by stinkeye on 2012-11-23
> **2F4U said:**
> Is this a fresh install or an upgrade? Do you have the problems from the beginning? If it works for other users, it is likely that some settings for this particular user are the problem.
You can try 

unity --reset

in a terminal.
unity --reset
does not work in 12.10

Reset compiz to default...
```
dconf reset -f /org/compiz/
```

Then reload with...
```
setsid unity
```
or
Log out/in

---

### Post by pc10pc on 2012-11-24
thanks for the replys i'll reset compiz and see how it goes.

---

### Post by pc10pc on 2012-12-01
a week on and unity is starting every time, thanks

---


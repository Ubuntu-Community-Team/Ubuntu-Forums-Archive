---
title: "Racer"
date: 2007-06-24
forum: Gaming &amp; Leisure
---

### Post by dr_psikick on 2007-06-24
This is not really a question about gaming, more about hardware, but it&#347; gaming related...
In the game Racer - Free driving simulation, my USB wheel is not detected, because is assigned to /dev/input/js0, and Racer searches for /dev/input/js1. In previous Ubuntu versions, i copy js0 and pasted it as js1, and the problem was solved. Now in the Feisty version i am not able to do that... Does someone know any procedure to resolve this?

thanks,
Helder Correia

---

### Post by Cappy on 2007-06-24
This may not work but how about:
```
sudo ln -s /dev/input/js0 /dev/input/js1
```
I assume that "/dev/input/js1" doesn't exist

---

### Post by dr_psikick on 2007-06-24
> **Cappy said:**
> This may not work but how about:
```
sudo ln -s /dev/input/js0 /dev/input/js1
```
I assume that "/dev/input/js1" doesn't exist

Yes, I did try that... but thanks anyaway ;)

---

### Post by dr_psikick on 2007-06-25
no other ideas?:(
ok, thanks anyaway!:p

---


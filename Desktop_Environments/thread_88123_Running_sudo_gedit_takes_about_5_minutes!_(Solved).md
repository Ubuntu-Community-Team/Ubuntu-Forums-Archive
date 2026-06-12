---
title: "Running sudo gedit takes about 5 minutes! (Solved)"
date: 2005-11-09
forum: Desktop Environments
---

### Post by kreso on 2005-11-09
and strangly enough, when I disconnect eth0 it loads fine?

Also, totem doesnt load if eth0 is down... sigh... :)


Please, does anyone know a solution to this, it's driving me nuts :(

---

### Post by aysiu on 2005-11-09
I don't know a solution, but an easy workaround would be to ```
sudo nano
``` instead of ```
sudo gedit
```

---

### Post by kreso on 2005-11-09
it's the same with sudo nautilus :(

---

### Post by kreso on 2005-11-09
but what I dont understand is, what the heck does it have to do with eth0 being up or down???

---

### Post by flipkick on 2005-11-10
Change your password. Worked for me as I had the same problem.

---

### Post by kreso on 2005-11-10
nope, didnt help

---

### Post by ssam on 2005-11-10
what is the output from
```
ifconfig
```
?

it sounds like the loopback interface (lo) might not be up

try running

```
sudo ifup lo
```

---

### Post by aysiu on 2005-11-10
[QUOTE=kreso]it's the same with sudo nautilus :([/QUOTE] I didn't say *nautilus*. I said *nano*. Try ```
sudo nano *nameoffile*
```

---

### Post by kreso on 2005-11-11
yes, I know, I can use the nano editor instaead of gedit. but that's not the point. It's not just gedit that's the problem: It's gedit, nautilus and totem. Nautilus wont open for 5 minutes if eth0 is up, and totem/xine wont start if eth0 is down...

---

### Post by kreso on 2005-11-12
[QUOTE=ssam]what is the output from
```
ifconfig
```
?

it sounds like the loopback interface (lo) might not be up

try running

```
sudo ifup lo
```[/QUOTE]


Thanks a million! You've solved my problem!

Funny though, both eth0 and lo dont seem to come up at boot even though auto lo and auto eth0 is listed in /etc/network/interfaces?

---


---
title: "Dell Inspiron 1750 Dead slow, driver problem?"
date: 2012-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ljt3759 on 2012-04-16
Hey guys, I've just decided to start using Ubuntu again, first I'll give you my problems(s):

I'm dual booting along side windows 7 (I used wubi)

My computer is dead slow running ubuntu, which is strange since I have 4gb of ram with (I believe) a 2.1ghz processor (64 bit). 

I tried playing some games to see if they would be slow too, and they are, so I thought this might be a driver problem, I've gone into driver settings and it says "no propriety drivers are in use on this system" (I don't know what drivers I need either)

Also the mouse cursor has such a horrible movement and doesn't feel right at all, maybe this is related? I don't know all that much about Linux, only used it briefly before, now I'm in a bit of a pickle.

Any help would be amazing, thanks for your time.

---

### Post by ljt3759 on 2012-04-16
Also to add, when I go into driver settings, there are no drivers available to download, it's just a blank space.

---

### Post by ljt3759 on 2012-04-16
Bump ^

---

### Post by roelforg on 2012-04-16
> **ljt3759 said:**
> Bump ^
Give my some specs,
try running top in the terminal and see what's using the most cpu.

---

### Post by ljt3759 on 2012-04-17
PID: 1745
user: lewis
PR: 39
NI: 19
VIRT: 82836
RES: 48m
SHR: 3772
process is running
CPU%: 99%
mem: 1.2%
time+: 56:48.32
command: apt check

That's the process with the highest cpu usage.

Do you know what it is?

---

### Post by lisanels47 on 2012-04-18
Try killing its PID.  

kill 1745  (or whatever PID it is now)

If it doesn't close, use

kill -9 1745  (or whatever PID it is now)

Does that make it snap out of it and run better?

What's the output from 'ps -ef | grep 1745'

---

### Post by ljt3759 on 2012-04-22
I deleted my wubi installation and am now using a proper dual boot install, onto futher problems though!

---


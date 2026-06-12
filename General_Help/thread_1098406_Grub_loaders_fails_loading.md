---
title: "Grub loaders fails loading"
date: 2009-03-17
forum: General Help
---

### Post by quirijnquintus on 2009-03-17
Just one of the many problems I have with Ubuntu :(

When I start up my laptop, most of the time the Grub Loader just fails to run. After the BIOS screens, when you suppose to see the Grub screen, there is just a cursor flasing on and off: _ 
 
Nothing loads and you cannot enter commands whatsoever. Sometimes I have to restart 3 times before it enters the Loader! 

Anyone had the same probs? Or would know a solution?

[SIZE="2"]Iam running:
Fujitsu Siemens Amilo L1310G
1.60Ghz Celeron
512DDR RAM
80GB HDD[/SIZE]

---

### Post by ruel- on 2009-03-17
does it return any error codes?

usually when grub fails to load, it returns error codes like, 21, 16, 17, etc..

---

### Post by cariboo on 2009-03-17
It sounds like you may have a poor connection to your hard drive, open up the door on the bottom and make sure the drive is seated completely.

Note: make sure your laptop is turned off, not in suspend mode

Jim

---

### Post by quirijnquintus on 2009-03-17
> **ruel- said:**
> does it return any error codes?

No errors whatshoever, just a flashing cursor

@cariboo What do you mean by seated completely?

---

### Post by quirijnquintus on 2009-03-18
> **cariboo907 said:**
> It sounds like you may have a poor connection to your hard drive

btw, when I run speedfan in windows and use the s.m.a.r.t. function. It reports that it is in good condition, fitness and performance are almost perfect.


[[IMG]http://img16.imageshack.us/img16/892/speedfann.th.jpg[/IMG]](http://img16.imageshack.us/my.php?image=speedfann.jpg)

---

### Post by geometry_quiz on 2009-03-18
does it just do this on occasion or is it something that is constantly going on?

---

### Post by quirijnquintus on 2009-03-19
It WAS most of the time I turned my laptop on. 

BUT I think i found the source of the problem, I think it's my external HDD which interferces somehow with the grub loader or with Master boot. because since I have it disconnected at start up it works perfectly.

The external hard drive is from LaCie 320GB.

I think we can consider this solved :)

---


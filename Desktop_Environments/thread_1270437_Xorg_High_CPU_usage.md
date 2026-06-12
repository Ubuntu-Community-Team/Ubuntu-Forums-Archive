---
title: "Xorg High CPU usage"
date: 2009-09-19
forum: Desktop Environments
---

### Post by serlex on 2009-09-19
I have

[LIST]
[*]Dell inspiron 6000
[*]Ati x300
[*]ATI Catalyst™ 9.3 Proprietary Linux x86 Display Driver
Visual Effects: None
[/LIST]

I do 'top' and CPU is Xorg 80%+ on idle, I have not configured xorg.conf.

Any ideas?

Thank you

---

### Post by shae on 2009-09-19
Are you currently using compiz?

---

### Post by serlex on 2009-09-20
I'm not using compiz

Any ideas?

---

### Post by londonali1010 on 2009-09-20
I've heard that there's a mempry leak in Xorg when using Firefox + Flash plugin, and just shutting down Firefox doesn't help, you have to restart X. I'm sorry I haven't got any more details, but it should get you started where to look.

---

### Post by serlex on 2009-09-21
I have disabled Adobe Flash on FF, still xorg on 80% on idle

---

### Post by Lars Noodén on 2009-09-21
I get the same problems sometimes on the latest development version of Karmic.  I do not have flash installed.  Restarting X and KDM does not help. 

$ lsb_release -rd
Description:    Ubuntu karmic (development branch)
Release:        9.10

---

### Post by krazyd on 2009-09-21
try removing the fglrx driver and using the default radeon open source driver instead.

---

### Post by serlex on 2009-09-21
Yep, think you were correct krazyd

Solved through this tutorial

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---


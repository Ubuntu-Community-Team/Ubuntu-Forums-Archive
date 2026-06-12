---
title: "How to start in console mode?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by stoyanmihaylov on 2010-05-01
Before it was easy - I removed gdm and kdm and my laptop started in console mode.
Now I would like to get same thing - I made upgrade to ubuntu 10.4 and it starts again in graphics mode. I removed from grub menu.lst splash and quit, removed gdm and kdm - and again I receive graphics prompt.
PS
I removed also failsafe-x.

---

### Post by wojox on 2010-05-01
Where you removed splash and quit put in **text** see if that helps it?

---

### Post by stoyanmihaylov on 2010-05-03
Thanks.
I saw something starts gdm - and this make me very unhappy - before we had a chance to control services through /etc/rcX
Now I have no idea how I could control those services.

---

### Post by sisco311 on 2010-05-03
> **stoyanmihaylov said:**
> Thanks.
I saw something starts gdm - and this make me very unhappy - before we had a chance to control services through /etc/rcX
Now I have no idea how I could control those services.

Some (most) of the System-V style init scripts were replaced by Upstart jobs (/etc/init).

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)

---

### Post by stoyanmihaylov on 2010-05-03
Thanks - I will look there. 
By the way - putting text - cause starting in text mode.

---

### Post by jcglt on 2010-05-03
Similar problem here : I cannot start in console mode and I cannot even start in recovery mode where I get a "zebra" like unsynchronized screen. I get the same zebra screen when I hit CTRL+ALT+F1 to 6 from a graphic mode screen, which meens my laptop (SIS Mirage 3 graphics) does not work anymore in console mode since I upgrades from 9.10 to 10.04.

---

### Post by stoyanmihaylov on 2010-05-07
> **jcglt said:**
> Similar problem here : I cannot start in console mode and I cannot even start in recovery mode where I get a "zebra" like unsynchronized screen. I get the same zebra screen when I hit CTRL+ALT+F1 to 6 from a graphic mode screen, which meens my laptop (SIS Mirage 3 graphics) does not work anymore in console mode since I upgrades from 9.10 to 10.04.

I got some more suggestions - kernel mode settings. You can forbid them and then you should start in normal console. But how to forbid - check google.

---


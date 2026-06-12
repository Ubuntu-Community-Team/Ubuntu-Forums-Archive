---
title: "LCD brightness adjusting"
date: 2008-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dimafogo on 2008-08-11
Hi all,

after I upgraded my Ubuntu installation on Dell Inpiron 1501 (6400) to v8.04 I can't smoothly adjust brightness of the screeen using hotkeys [Fn]+[Up/Down], it can be only set in one of  three levels (full brightness, 50% bright, low brightness). Is it possible to add some more intermediate levels?

Regards,
Dima

---

### Post by Teamgeist on 2008-08-11
I had the same problem with my XPS m1330.
Try the following:

```
sudo gedit /etc/modprobe.d/blacklist 
```

At the end add a line looking like this:

```
blacklist video
```

Then save the file and after a reboot, it should work.
Well at least it did on my machine.

Good Luck.

---

### Post by dimafogo on 2008-08-16
**Teamgeist**, thanks a lot, it worked on my Inspiron 1501 too!

---

### Post by meborc on 2008-08-18
thanks, worked on my 1520 as well ;)

---

### Post by zeroed on 2008-09-01
Doesn't work for me.

Bios 2.6.3

---

### Post by findepi on 2008-11-01
great thanks!
Are there any side effects? Indeed, what are we blacklisting?

---

### Post by TechieAu on 2008-11-08
> **findepi said:**
> great thanks!
Are there any side effects? Indeed, what are we blacklisting?

It did have a side effect for me, pretty nasty one! After disabling "video" as advised above, once I adjusted the brightness, the keyboard stopped working as well as taskbar and right-click menus.

---


---
title: "compiz fusion is installed, but no effects working"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by shorty28898 on 2007-08-19
why dont any of the effects work?  i can go to the compiz config settings manager, and it has all the icons and check marks, but none of those effects are working :-\

---

### Post by GFree678 on 2007-08-19
> **shorty28898 said:**
> why dont any of the effects work?  i can go to the compiz config settings manager, and it has all the icons and check marks, but none of those effects are working :-\
You're the guy who complained about how hard it is to install Linux software right? :)

Anyways, sounds like you installed it but didn't actually start it. Open a terminal and type

compiz --replace -c emerald &

Should startup all the effects provided xorg has composite enabled (and provided you've installed emerald).

---

### Post by Rupertronco on 2007-08-19
Also, make sure you have the updated drivers for your video card to ensure compiz won't crash on you.

---

### Post by shorty28898 on 2007-08-19
how do i know if my driver is up to date? and when i did that .. this came up
[1] 6373
lindo@ubuntu:~$ Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

---


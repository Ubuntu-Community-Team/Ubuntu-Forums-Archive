---
title: "Help - jack, ripping tool"
date: 2006-08-14
forum: Desktop Environments
---

### Post by edric on 2006-08-14
I'm using jack (wich i've found in the dapper repository) to rip some cd.
I edited /etc/jackrc to my tastes for making ogg and it works great but the man pages don't explain how to modify it for mp3 (lame).

Someone could help me? :)

---

### Post by corney91 on 2007-06-16
In jackrc, or .jack3rc if you copied it to your home folder, where line 25 reads:
```
#encoder:oggenc
```
Change this so it reads:
```
encoder:lame
```
And it should use lame to convert. Make sure you have lame installed.

---


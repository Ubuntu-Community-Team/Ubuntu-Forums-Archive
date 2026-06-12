---
title: "help get my gui back.."
date: 2005-09-08
forum: Desktop Environments
---

### Post by floyd27 on 2005-09-08
Hi.
I was trying to get my ati drivers to work..
Ended up messing up everything.

I tried dpkg-reconfigure xserver-org in recovery mode. (this usually works)

and
xresprobe

but it says i dont have xserver-org installed or it is broken...
 does anyone know how to get it back?
i tried "aptitude" and updated everything but it wont let me install anything from there?

---

### Post by floyd27 on 2005-09-08
got it

i did 
```
sudo apt-get install ubuntu-desktop
```

then it gave an error saying to install something else (its written h=there)
then 
```
xorgconfig
```

restart and it worked...

---

### Post by floyd27 on 2005-09-08
guess thats not how to add code..

```
test
```

---


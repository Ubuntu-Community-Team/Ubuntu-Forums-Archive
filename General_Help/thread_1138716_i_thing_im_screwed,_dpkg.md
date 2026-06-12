---
title: "i thing im screwed, dpkg?"
date: 2009-04-26
forum: General Help
---

### Post by mr.Hsmith on 2009-04-26
im new to ubuntu, just got version 8.0.4, when i try to download the updates i get this

[[IMG]http://www.freeimagehosting.net/uploads/0b7ded7f12.png[/IMG]]("http://www.freeimagehosting.net/")
pleas help, thank you

---

### Post by kellemes on 2009-04-26
From a terminal window, start typing..
```
sudo dpkg --configure -a
```
Hit ENTER and enter password..

---

### Post by mr.Hsmith on 2009-04-26
thanks!, now its saying i have a broken package, and to use the broken filter to fix, how do i do that?

---

### Post by oldos2er on 2009-04-26
> **mr.Hsmith said:**
> thanks!, now its saying i have a broken package, and to use the broken filter to fix, how do i do that?

 Run
```
sudo apt-get install -f
```

---


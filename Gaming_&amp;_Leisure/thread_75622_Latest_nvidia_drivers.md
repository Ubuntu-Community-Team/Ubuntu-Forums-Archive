---
title: "Latest nvidia drivers"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by idn on 2005-10-13
Has anyone managed to install the latest nvidia drivers, I tried today but I got an error because of the GCC version being used.

I need to install the latest ones because I have a 78000gtx

cheers

---

### Post by professor_chaos on 2005-10-13
yes you just have to set the variable for gcc-3.4 by, ```
export CC=gcc-3.4
```

---

### Post by idn on 2005-10-14
do I just type that from the command line before I run the installer?

Thanks for your reply

---

### Post by wylfing on 2005-10-14
Yep, just type that in.

---

### Post by idn on 2005-10-14
[n00b] I guess I need to sudo apt-get install gcc-3.4 as well? [/n00b]

---

### Post by idn on 2005-10-14
woot! Works now

Maybe someone should write a howto for breezy to install the drivers like someone did for hoary...

Thanks guys for the help

---

### Post by officeboy on 2005-10-14
like this?
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---


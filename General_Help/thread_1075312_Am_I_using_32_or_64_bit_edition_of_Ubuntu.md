---
title: "Am I using 32 or 64 bit edition of Ubuntu"
date: 2009-02-20
forum: General Help
---

### Post by Openrulers on 2009-02-20
I tried various command to find that
like
cat /etc/issue
cat /etc/lsb-release

I checked in system tools and under tab system
which shows 
Ubuntu 8.10
Kernel Linux 2.6.27-12-generic
Gnome 2.24.1

Please help

---

### Post by Kevbert on 2009-02-20
Try the following in Applications-Accessories-Terminal
```
uname -a
```
If it displays x86_64 you're using 64 bit Ubuntu, if not it's only 32 bit.

---

### Post by howefield on 2009-02-20
Open a terminal and type
```

uname -m
```

What does it return ?

---

### Post by JohnDocHoliday on 2009-02-20
The easiest way: just look for a /dev64 directory. If you have one in the root, you're using a 64bit system. ;)

---

### Post by howefield on 2009-02-20
> **JohnDocHoliday said:**
> The easiest way: just look for a /dev64 directory. If you have one in the root, you're using a 64bit system. ;)

You sure about that ?

I don't and I am... ;)

---

### Post by 3rdalbum on 2009-02-20
I think JohnDocHoliday is referring to "/lib32" and "/lib64". The /lib64 is just a symlink to /lib.

---

### Post by JohnDocHoliday on 2009-02-20
Damn, I hate mornings... :D

---

### Post by binbash on 2009-02-20
Check the output of uname -m if you see i686 etc it is 32 if you see x86_64 etc it is 64

---

### Post by linux_tech on 2009-02-20
what is output of
```
uname -a
```

---


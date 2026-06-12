---
title: "where to check OS version"
date: 2009-04-30
forum: General Help
---

### Post by gorucan on 2009-04-30
hi

i'd like to know how i check whether installed version of interpid or jaunty is 32-bit or 64-bit because i forgot which one i installed !

thanks,
j.

---

### Post by _Purple_ on 2009-04-30
[http://ubuntuforums.org/showthread.php?p=7177216#post7177216](http://ubuntuforums.org/showthread.php?p=7177216#post7177216)

---

### Post by sisco311 on 2009-04-30
```
lsb_release -a
```
```
uname -a
```

x86_64 = 64bit
i386, i486, i586 ... = 32bit

---

### Post by gorucan on 2009-04-30
> **sisco311 said:**
> ```
lsb_release -a
```
```
uname -a
```

x86_64 = 64bit
i386, i486, i586 ... = 32bit
ty !

---


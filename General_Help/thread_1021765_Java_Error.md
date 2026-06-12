---
title: "Java Error"
date: 2008-12-25
forum: General Help
---

### Post by GophX on 2008-12-25
I am using ubuntu 8.10.
I am constantly getting "java" related errors.
Whenever I install something, for some reason I get a java error.
I figured there must have been a corruption in the installation of java.
So I went to uninstal java so I could re-instal it and got this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I went to the terminal, typed: sudo dpkg --configure -a
And got this error:

```
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```

Any help on this issue would be much appreciated. 
Cheers :)

---

### Post by GophX on 2008-12-25
Here is the error I recieve every time I install something new:

E: java-common: package java-common is not ready for configuration

---

### Post by GophX on 2008-12-26
Bump.... ;)

---

### Post by Rog-Mahal on 2008-12-26
How are you attempting to install java? I've found that the easiest way is to go through Add/Remove Programs in the Applications menu. Search for java. I've had little problem with the IcedTea JRE and plugin.

---

### Post by GophX on 2008-12-26
I Installed jave via the Add/Remove Programs.
I think the install got corrupted because I didn't have enough hdd space to install it fully.
I tried to uninstall and I got the errors I posted above.

---

### Post by GophX on 2008-12-27
Bumb... Any Ideas? :P

---

### Post by jamesstansell on 2008-12-27
I guess something is wrong with your dpkg or with the db it maintains.  But sorry, no suggestions for what to do.

---


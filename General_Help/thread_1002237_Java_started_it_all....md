---
title: "Java started it all..."
date: 2008-12-04
forum: General Help
---

### Post by LightHeart on 2008-12-04
Hey guys, i just installed java in the terminal and i got to a page of agreement the contract. Their was nothing to go forward and such and so i thought i was done so i closed it. Now i try to go to synaptic and i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What should i do?

---

### Post by falcon61102 on 2008-12-04
Have you tried running that command in the Terminal?

That should reload the configuration for the package manager and hopefully allow you to access it again.

---

### Post by kostkon on 2008-12-04
> **LightHeart said:**
> Hey guys, i just installed java in the terminal and i got to a page of agreement the contract. Their was nothing to go forward and such and so i thought i was done so i closed it. Now i try to go to synaptic and i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What should i do?
Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

---

### Post by LightHeart on 2008-12-04
well i did that now it says i have 1 broken package, use the broken filter to find it! How do i do that?

---

### Post by alzie on 2008-12-04
System>Administration>Synaptic Package Manager,  then

Edit> Fix Broken Packages

That should do it.

---

### Post by LightHeart on 2008-12-04
the problem is when i go to snaptic thats where the error pops up. Nevermind i got it, thank you all!

---

### Post by falcon61102 on 2008-12-04
Glad you got it working.  Make sure you mark the thread solved using the Thread Tools in the upper right.

---


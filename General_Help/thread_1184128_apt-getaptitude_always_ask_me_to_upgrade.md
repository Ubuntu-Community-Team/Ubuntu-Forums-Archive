---
title: "apt-get/aptitude always ask me to upgrade"
date: 2009-06-10
forum: General Help
---

### Post by cybertooth on 2009-06-10
Hi,

  I install lighttpd by using deb-src packages of debian ..
the reason i did that is to patch a certain module to lighttpd because it is not included from the default package..

I built and successfully installed it ... but everytime I use aptitude update and upgrade
lighttpd needs to be upgraded ... it just the same version to what I already have. 
I just compiled it using debian-src repo ...

need some help.
thanks..

---

### Post by colau on 2009-06-10
> **cybertooth said:**
> Hi,

  I install lighttpd by using deb-src packages of debian ..
the reason i did that is to patch a certain module to lighttpd because it is not included from the default package..

I built and successfully installed it ... but everytime I use aptitude update and upgrade
lighttpd needs to be upgraded ... it just the same version to what I already have. 
I just compiled it using debian-src repo ...

need some help.
thanks..
What's the version?
```

lighttpd --v

```
:(

---

### Post by cybertooth on 2009-06-10
its 
lighttpd-1.4.19


cant find any solution in the web :(

---

### Post by louieb on 2009-06-10
Look for the package in Synaptic. There is a way to pin or lock a program to a specific version. Been a while since I've had to do it. Just look around the menus.

---

### Post by cybertooth on 2009-06-10
thanks for the reply

Im in a SSH .. how do I use synaptic?

is there any manual command for that?

---

### Post by louieb on 2009-06-11
use aptitude.   

```
man aptitude  
```

some of the options you might want to look at are **keep, hold, and forbid-version**.

---


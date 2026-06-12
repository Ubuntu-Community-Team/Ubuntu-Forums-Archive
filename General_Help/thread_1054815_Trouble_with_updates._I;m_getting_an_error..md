---
title: "Trouble with updates. I;m getting an error."
date: 2009-01-30
forum: General Help
---

### Post by princerameses on 2009-01-30
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and when I try to install a program it says I need to close update manager.

---

### Post by earthpigg on 2009-01-30
did you try running dpkg as described in a terminal?

iirc, i had this problem before, and thats all i did and it worked...

---

### Post by princerameses on 2009-01-30
> **earthpigg said:**
> did you try running dpkg as described in a terminal?

iirc, i had this problem before, and thats all i did and it worked...



When I try I get: dpkg: requested operation requires superuser privilege

---

### Post by plucky on 2009-01-30
> **princerameses said:**
> When I try I get: dpkg: requested operation requires superuser privilege

```
sudo dpkg --configure -a
``` will give you the required privileges after you input your login password.It will not echo as you type.

Good Luck

---

### Post by princerameses on 2009-01-30
Ok. It now says I have a broken something when I go to synaptic. It is sun java. (sun-java6-jre) What do I do now?

---

### Post by plucky on 2009-01-30
> **princerameses said:**
> Ok. It now says I have a broken something when I go to synaptic. It is sun java. (sun-java6-jre) What do I do now?

In Synaptic **Edit > Fix Broken Packages** For Sun-Java , you have to accept their agreement when the package is installing.


Or open a terminal and use ```
sudo apt-get install -f
``` and again be prepared to accept the Sun-java agreement.

Good Luck

---

### Post by princerameses on 2009-01-30
Ok, that worked. Much Thanks. :KS

---

### Post by jespdj on 2009-01-30
In Synaptic, try **Edit > Fix Broken Packages**

*edit*: too late... ;)

---


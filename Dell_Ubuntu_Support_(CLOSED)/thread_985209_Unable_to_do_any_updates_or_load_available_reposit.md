---
title: "Unable to do any updates or load available repository index? (Mini 9)"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gavinfoxx on 2008-11-17
Hi all, I dont know WHAT I did with my mini 9, but I havent been able to really update ANYTHING for about 28 days... and I have no idea why... I think I accidentally deleted the links to the dell third party stuff.. can anyone help me get that back, or figure out what I have to do?

Im still running 8.04... thanks!

---

### Post by gavinfoxx on 2008-11-19
Can anyone help...?

---

### Post by bd_thompson on 2008-11-19
> **gavinfoxx said:**
> Can anyone help...?

SYSTEM > ADMINISTRATION > SOFTWARE SOURCES 

Choose 3rd Party Tab.  Check all the Dell resources.

---

### Post by gavinfoxx on 2008-11-19
> **bd_thompson said:**
> SYSTEM > ADMINISTRATION > SOFTWARE SOURCES 

Choose 3rd Party Tab.  Check all the Dell resources.


Yea, I think I deleted them.  It seemed like a good idea at the time, I was getting some sort of error with them (I cant remember what it was...) can someone give me the list of those?

---

### Post by yakker.yak on 2008-11-20
> **gavinfoxx said:**
> Yea, I think I deleted them.  It seemed like a good idea at the time, I was getting some sort of error with them (I cant remember what it was...) can someone give me the list of those?

Here are the contents of the default Dell Ubuntu /etc/apt/sources.list

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

```
You can open up a terminal (Accessories->Terminal) and type:

```
sudo gedit /etc/apt/sources.list
```

to edit the file and copy-and-paste the above into the file.

---

### Post by gbowman2412 on 2009-04-06
I had the same issue and this worked for me

---


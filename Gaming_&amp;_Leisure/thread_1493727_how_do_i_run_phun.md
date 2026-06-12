---
title: "how do i run phun???"
date: 2010-05-26
forum: Gaming &amp; Leisure
---

### Post by killer64 on 2010-05-26
i cant run phun at all, it keeps saying i need libpng3 witch i already have is there a special directory i need to put the folder in? i am running ubuntu 10.04 all the other threads i found either didn't work, locked randomly by an admin , wasn't the problem i had, or it wasn't the right OS

---

### Post by Sealbhach on 2010-05-26
Hi,
If I were you I would add the repo for GetDeb. Just add this line to the end of your software sources:

```
gksu gedit /etc/apt/sources.list
```Add this

```
deb http://archive.getdeb.net/ubuntu lucid-getdeb games
```

Save and close. Then

```
sudo apt-get update
``````

sudo apt-get install phun

```This works for me.
.

---

### Post by Kevbo on 2010-12-07
Thanks.  Worked great.  You just made my daughter very happy.  And therefore, me too. :D

---


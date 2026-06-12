---
title: "sources.list file contents"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mtbiker on 2006-07-16
hello,
  I messed up yesterday and wrote of the original Sources.list file.  Could one of you post the original content of it here so I can recreate it?

Thanks!

---

### Post by timetunnel on 2006-07-16
Well, this is not the "original" source.list after a fresh install, but all dapper repos are in here (plus some extra at the bottom). This is from a German install, therefore all the "//de.archive...." thingies (replace with appropriate county is applicable):

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ dapper-proposed main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-proposed main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
# deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
# deb http://seveas.theplayboymansion.net/seveas dapper-seveas drivers
deb http://wine.budgetdedicated.com/apt dapper main
 
```

---

### Post by bluecherry on 2006-07-16
Hi,

try: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

This generates (depending on what you select) a sources.list including official, non-official and other interesting repo's (see descriptions).

Grtz,

Timo

---

### Post by tzulberti on 2006-07-16
Thanks bluecherry, that was an excelent link to be added to bookmarks.

---

### Post by mtbiker on 2006-07-16
Thanks guys!

---


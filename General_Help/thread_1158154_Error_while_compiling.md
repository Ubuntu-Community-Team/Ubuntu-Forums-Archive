---
title: "Error while compiling"
date: 2009-05-13
forum: General Help
---

### Post by Adiko on 2009-05-13
When im usnig that comand:
> ./configure --enable-mysql --enable-sqlite --enable-remote-control --enable-server-diag
im getting that error...
> hecking for main in -lboost_regex-gcc-mt... no
checking for main in -lboost_regex-mt... yes
checking for main in -lboost_system-gcc-mt... no
checking for main in -lboost_system-mt... yes
checking for main in -lboost_date_time-gcc-mt... no
checking for main in -lboost_date_time-mt... no
checking for main in -lboost_date_time... no
configure: error: "Linking against boost::date-time library failed."


Im new user of ubuntu so please tell me exactly what should i do

---

### Post by oldos2er on 2009-05-13
What program are you trying to compile?

---

### Post by Adiko on 2009-05-13
Its open tibia server. Exactly TheForgotten Server 0.3.1 pl2

---

### Post by Adiko on 2009-05-13
refresh

---

### Post by oldos2er on 2009-05-13
Looks like you're missing a dependency. Is there a README with the source code?

---

### Post by Yellow Pasque on 2009-05-13
You need some sort of libboost-dev package (and probably a bunch of other -dev packages). There's a few versions of libboost available in Jaunty. The "officially supported" one is libboost1.35
```
sudo apt-get install libboost1.35-dev
```

It would be best to read the documentation, figure out what dependencies you need, and get the dependencies you need. Or you can just keep running ./configure and grabbing whatever -dev package it complains about until you can run it without errors.

---


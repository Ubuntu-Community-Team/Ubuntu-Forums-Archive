---
title: "Locate"
date: 2005-10-14
forum: Desktop Environments
---

### Post by dbee on 2005-10-14
Why does locate keep bringing up files and folders that are no longer on the system ?

locate / --name apache2

gives me a bunch of false positives, and if I try to stat them I get 

No such file or directory

---

### Post by grj on 2005-10-14
I use slocate, but I think locate also has to have the database updated with:

sudo updatedb

---

### Post by dbee on 2005-10-15
:cool:

---


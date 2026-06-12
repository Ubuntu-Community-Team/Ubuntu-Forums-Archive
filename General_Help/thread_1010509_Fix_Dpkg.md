---
title: "Fix Dpkg"
date: 2008-12-13
forum: General Help
---

### Post by gletob on 2008-12-13
I was wondering what command runs when you select the "fix dpkg" option in recovery mode?

---

### Post by Izek on 2008-12-13
It runs fix dpkg ;)

---

### Post by gletob on 2008-12-13
No I want to know what command it runs so I can run it from a terminal.

---

### Post by gletob on 2008-12-14
Anyone?

---

### Post by linux_tech on 2008-12-14
Just a guess but probably something along the lines of
```
apt-get update
sudo apt-get clean
sudo apt-get install -f
sudo dpkg --configure -a
apt-get dist-upgrade
```

---


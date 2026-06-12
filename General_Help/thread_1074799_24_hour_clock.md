---
title: "24 hour clock"
date: 2009-02-19
forum: General Help
---

### Post by shmoesus on 2009-02-19
how do i create a shell script that will display a 24 hour clock by hour, minutes, seconds. this should take up most of the display screen and can be run as a process?

thanks

---

### Post by Dr Small on 2009-02-19
```
while true; do clear; date +%T | figlet -c; sleep 1; done
```

---

### Post by bapoumba on 2009-02-19
Moved to General Help.

---

### Post by shmoesus on 2009-02-19
sorry that command dosent work ohh, btw im using ubuntu 8.10

---

### Post by Dr Small on 2009-02-19
> **shmoesus said:**
> sorry that command dosent work ohh, btw im using ubuntu 8.10
It probably doesn't work because you don't have figlet installed.
```
sudo apt-get install figlet
```

---


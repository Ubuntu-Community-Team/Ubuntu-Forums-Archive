---
title: "c compiler"
date: 2006-01-07
forum: Desktop Environments
---

### Post by derm0 on 2006-01-07
Hi,
I was wondering how to compile a c program in Ubuntu Linux as the regular gcc command doesn't seem to work??
Thanks,
Derm

---

### Post by taurus on 2006-01-07
You probably don't have a gcc installed on your machine!  Therefore, you need to install it first by running

sudo apt-get update
sudo apt-get install build-essential

Then, just compile your c program away as

gcc program.c

---

### Post by TimonVO on 2006-01-07
these three commands compile almost any language using GCC:
```
$./configure
$make
#make install
```

---

### Post by derm0 on 2006-01-07
Thanks guys - thats a great help!!

---

### Post by kurei on 2006-01-07
I'm also get a error about C compiler

---


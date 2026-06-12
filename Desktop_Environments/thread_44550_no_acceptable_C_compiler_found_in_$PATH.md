---
title: "no acceptable C compiler found in $PATH"
date: 2005-06-26
forum: Desktop Environments
---

### Post by podrik0 on 2005-06-26
Hi 
getting the following when I type ./configure which I have to do before I make:

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Anyone help me out please!!!!

Its for my sagem modem so its vital, as I'm trying to get on the net so I can delete this windows crap.

Thanks

---

### Post by Xian on 2005-06-26
Open a terminal and install the build essential tools:
```
$ sudo apt-get install build-essential
```

---


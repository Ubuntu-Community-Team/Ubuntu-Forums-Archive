---
title: "[SOLVED] Intrepid: is parted broken too?"
date: 2009-01-07
forum: General Help
---

### Post by NT4usB on 2009-01-07
It used to have an interactive mode...
```
ct@p42:~$ man parted | grep interactive
       -i, --interactive
ct@p42:~$ 
``````
ct@p42:~$ sudo parted -i
Usage: parted [-hlmsv] [DEVICE [COMMAND [PARAMETERS]]...]
ct@p42:~$ 

```

---

### Post by dcstar on 2009-01-07
> **NT4usB said:**
> It used to have an interactive mode...
```
ct@p42:~$ man parted | grep interactive
       -i, --interactive
ct@p42:~$ 
``````
ct@p42:~$ sudo parted -i
Usage: parted [-hlmsv] [DEVICE [COMMAND [PARAMETERS]]...]
ct@p42:~$ 

```

It may well be, the -i option works on my 8.04 system.

Report it as a bug.

---

### Post by NT4usB on 2009-01-07
Upon further review...
It appears only man is broke.
Interactive is now the default, -i is no longer required.

---

### Post by NT4usB on 2009-01-07
Upon further review...
It appears only man is broke.
Interactive is now the default, -i is no longer required.

---


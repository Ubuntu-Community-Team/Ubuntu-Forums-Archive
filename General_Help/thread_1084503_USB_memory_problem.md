---
title: "USB memory problem"
date: 2009-03-02
forum: General Help
---

### Post by 3layn on 2009-03-02
Hi !

Yesterday i tried to fill my usb memory stick (kingston datatraveler 2gb) with some data, and even tough i had 2 gb of memory free on the stick Ubuntu told me that i had 91 mb free.

Anyone knows of this problem?

---

### Post by abhilashm86 on 2009-03-02
had you done any partition to flash drive before?
check this from terminal
```

sudo fdisk -l

```
it gives information of flash drive, it will be named as sdb or sdb1............

---

### Post by razy60 on 2009-03-02
does that stick have something like U3 or a security vault application in it, if so you may need to reformat the stick (try fat 32). One other thing that can cause a problem is has the stick been used in a windows Pc and was it used as memory boost.

Raz

---

### Post by anaconda on 2009-03-02
have you emptied the .Trash from your USB memory?

---

### Post by 3layn on 2009-03-02
> **anaconda said:**
> have you emptied the .Trash from your USB memory?

Actually i have not tried anything of above mentioned. I will do as soon as im home from work this afternoon.

Thanks all for your fast reply  :KS

---


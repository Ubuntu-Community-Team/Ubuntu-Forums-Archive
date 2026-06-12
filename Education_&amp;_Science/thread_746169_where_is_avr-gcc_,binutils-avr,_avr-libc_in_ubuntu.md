---
title: "where is avr-gcc ,binutils-avr, avr-libc in ubuntu7.10"
date: 2008-04-05
forum: Education &amp; Science
---

### Post by amarender on 2008-04-05
i am cross compiling avr code on ubuntu 7.10 PC.
in the MAKEFILE i've supply

like this
 DIRAVR = /-----/----------
 DIRAVRBINUTILS = /--------/------
 DIRAVRLIB = /---------/-----------

So what should i substitute in the place of /---------/-----------/------....

---

### Post by thisismalhotra on 2008-04-07
Try following commands:-

```
sudo updatedb
locate <what you want?>
```

Post again if you dont get what you want?? You might wanna look in synaptic and see if the lib are installed. Also, please install a package called build-essential before you compile anything.

Compilers are not packaged by default in ubuntu.

---

### Post by amarender on 2008-04-09
synaptic showing these are installed but i want a purticuler location of these to invoke binaries from makefile

---

### Post by thisismalhotra on 2008-04-09
> **amarender said:**
> synaptic showing these are installed but i want a purticuler location of these to invoke binaries from makefile

I would use locate but update the db first and see if it works for you...

```
sudo updatedb
locate <what you want?>
```

---


---
title: "Need write permission"
date: 2008-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stfarm on 2008-12-23
Hi,

just got a Dell Mini (Inspiron) with Ubuntu 8.04.

The sound does not work, so I found a way to fix that but I nee to make a change to a file, and I do not have write accress.

How can I make the current user have full access, and/or how can I login as root to make those changes please.

I am sorry for such a basic question, but this is my first with this OS.

Thank you all,

Steve

---

### Post by iggykoopa on 2008-12-23
the command sudo will give you temporary root access, so to edit the file you need do:
```

sudo gedit [the name of the file]

```
you can use nano or whatever other program you want to actually edit the file, but gedit is good.

---

### Post by stfarm on 2008-12-23
Thank you very much, that worked great. A little inconvenient, but I guess I need to read up on how to work this one.

Steve

---

### Post by bd_thompson on 2008-12-23
> **stfarm said:**
> Thank you very much, that worked great. A little inconvenient, but I guess I need to read up on how to work this one.

Steve

You can also look under system tools.  You will find a root terminal you can use.

---


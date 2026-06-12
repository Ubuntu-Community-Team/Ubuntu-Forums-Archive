---
title: "how to test homemade SDDM theme for real w/o breaking computer?"
date: 2020-05-03
forum: Desktop Environments
---

### Post by anotherChris on 2020-05-03
My first attempt at doing something involving my own writing in a Linux system is making my own SDDM theme for Lubuntu 20.04.  I know about ```
sddm-greeter --test-mode
```  but it's not completely functional, so it's hard to tell if it will work and work correctly and consistently.  How do you test this before making it go live on your own computer?

---

### Post by Dennis N on 2020-05-03
I would install Lubuntu 20.04 in a virtual machine for your development purposes.

---

### Post by wildmanne39 on 2020-05-03
> **Dennis N said:**
> I would use install Lubuntu 20.04 in a virtual machine for your development purposes.

+1, I do all experimenting in virtual machines these days, years ago I use to experiment on my production machine on its bare metal hardware and I was constantly fixing what I had broken, with virtual machines just take a snapshot before you make any changes then if it goes wrong it only takes a few seconds to revert to a previous functioning instance of your OS.

---


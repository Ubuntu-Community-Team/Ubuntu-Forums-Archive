---
title: "Grub boot application?"
date: 2009-05-22
forum: General Help
---

### Post by Flexico on 2009-05-22
Is there a way to add a command to just run a single Linux application to my "/boot/grub/menu.lst" file? I'd like to be able to just run one of a number of programs without needing to boot up the whole system, if need be.

---

### Post by coffeecat on 2009-05-22
Simple answer: no. Grub is basically a bootloader - that's it - admittedly quite a sophisticated one. It doesn't have the code to be able to run applications. The only commands it can run are grub ones. See [here](http://www.gnu.org/software/grub/manual). Although there are quite a few commands, they all serve the same purpose - that of booting up an operating systems, which is what you need to run your applications.

---

### Post by kellemes on 2009-05-22
> **Flexico said:**
> Is there a way to add a command to just run a single Linux application to my "/boot/grub/menu.lst" file? I'd like to be able to just run one of a number of programs without needing to boot up the whole system, if need be.

coffeecat is correct.
You need a working system to have programs running.
You could focus on getting a working system that offers just enough for those programs to run, a little lighter and faster at boot.
Losing the login-manager (or choose a lighter alternative) and using a faster window-manager can change a lot.

---

### Post by Flexico on 2009-05-22
> **kellemes said:**
> coffeecat is correct.
You need a working system to have programs running.
You could focus on getting a working system that offers just enough for those programs to run, a little lighter and faster at boot.
Losing the login-manager (or choose a lighter alternative) and using a faster window-manager can change a lot.

How do I lose the login-manager? I only have one account set up for my laptop, so that would be great. :)

---


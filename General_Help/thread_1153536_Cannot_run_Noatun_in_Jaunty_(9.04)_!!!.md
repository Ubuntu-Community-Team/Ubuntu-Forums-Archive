---
title: "Cannot run Noatun in Jaunty (9.04) !!!"
date: 2009-05-08
forum: General Help
---

### Post by ram2500 on 2009-05-08
Hi there,
I cannot run Noatun in Jaunty 9.04. I do have it installed, but it will not run. When I choose it from the menu, it does nothing. In the terminal, it returns this message:

noatun: error while loading shared libraries: libartskde.so.1: cannot open shared object file: No such file or directory

I tried to look for libartskde.so.1 but I cannot find it. What can I do? I really like Noatun... Any help will be appreciated.

---

### Post by dcstar on 2009-05-08
> **ram2500 said:**
> Hi there,
I cannot run Noatun in Jaunty 9.04. I do have it installed, but it will not run. When I choose it from the menu, it does nothing. In the terminal, it returns this message:

noatun: error while loading shared libraries: libarts**kde**.so.1: cannot open shared object file: No such file or directory

I tried to look for libartskde.so.1 but I cannot find it. What can I do? I really like Noatun... Any help will be appreciated.

It looks like it requires a kde library, you have to find all dependencies and install them.

---


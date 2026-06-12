---
title: "uninstall self-compiled kernel"
date: 2009-02-18
forum: General Help
---

### Post by evrkusd on 2009-02-18
Hey
i'm running 8.10 and i recently tried to compile a kernel. i successfully installed it but for a number of reasons i need to uninstall it now. the kernel version is 2.6.28.5. it's not listed in synaptic and the sudo apt-get remove commands that i've tried so far haven't found the package (i don't even know what to call so i've just been basing it on what other kernels have been called) Anyone know how to do this? do i just have to delete the kernel files....?
thanks

---

### Post by evrkusd on 2009-02-19
nvm. $make clean from the /usr/src/linux-x-x-x-x and then deleting the files seems to be the best i can do.

---

### Post by sdennie on 2009-02-19
In the future, you should try to use make-kpkg to build kernels.  It will produce packages like the default Ubuntu kernels and you can use dpkg/apt to manage them.  A google search for make-kpkg will give you a lot of information on how to do that.

---


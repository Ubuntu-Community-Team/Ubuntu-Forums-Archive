---
title: "Kernel installation error"
date: 2009-01-21
forum: General Help
---

### Post by yoman82 on 2009-01-21
Using 9.04 beta, I've been experiencing two problems. One, my fglrx driver is not functional, and I receive an error whenever my computer boots. But this was to be expected. The other states that my kernel cannot be upgraded through update manager any more, there is a "Dependancy Error" Help would be appreciated.

---

### Post by gjoellee on 2009-01-21
> **yoman82 said:**
> Using 9.04 beta, I've been experiencing two problems. One, my fglrx driver is not functional, and I receive an error whenever my computer boots. But this was to be expected. The other states that my kernel cannot be upgraded through update manager any more, there is a "Dependancy Error" Help would be appreciated.

1. Ubuntu 9.04 Beta does not yet exist, tha latest Ubuntu is UBuntu 9.04 Alpha 3
2. Many drivers does still not work with the new kernel, you will most likely have to wait
3. There is a package that is needed for the kernel run fine. If you get the package name do "sudo apt-get install the-packagename"

You could compile the kernel yourself, look here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by yoman82 on 2009-01-21
No way in hell I'm compiling myself. I lack such expertise. Sorry, I'm using alpha, I suppose.
Anyway, the new kernel updates have been automatically installing for 18 months now, but suddenly they stopped. I can find the error, if you like.
****. The upgrade manager froze while performing a partial upgrade and I'm getting a new crash report every few seconds. Any help?

---

### Post by yoman82 on 2009-01-21
It says I need to use the --configure option on linux-restricted-modules-generic. How exactly do I go about doing this?

---

### Post by yoman82 on 2009-01-21
E: linux-image-2.6.27-11-generic: subprocess post-installation script returned error exit status 2
E: linux-image-2.6.28-4-generic: subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.28-4-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules: dependency problems - leaving unconfigured
Error log

---


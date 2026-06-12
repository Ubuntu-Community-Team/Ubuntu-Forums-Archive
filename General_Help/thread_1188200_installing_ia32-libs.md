---
title: "installing ia32-libs"
date: 2009-06-15
forum: General Help
---

### Post by subjugater on 2009-06-15
I am trying to install the intel fortran compiler/ifort following what has been posted at

[http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort](http://ubuntuforums.org/showthread.php?t=1082782&highlight=ifort)

Before installing ifort, it seems that I need to first install the package ia32-libs. But I couldn't with the error message:

> kuan@kuan-desktop:~/Desktop/ifort/l_cprof_p_11.0.083$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs


Anybody can help? Thanks.

---

### Post by synapsys on 2009-06-15
[http://ubuntuforums.org/showthread.php?t=720732](http://ubuntuforums.org/showthread.php?t=720732)

---

### Post by subjugater on 2009-06-15
> **synapsys said:**
> [http://ubuntuforums.org/showthread.php?t=720732](http://ubuntuforums.org/showthread.php?t=720732)

Thanks, buddy. By reading what you suggested, I realized that I am using 32-bit system which may not be compatible with ia32-libs, even which is rather weird.

---


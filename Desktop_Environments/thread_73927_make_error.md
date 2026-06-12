---
title: "make error"
date: 2005-10-10
forum: Desktop Environments
---

### Post by paperdiesel on 2005-10-10
Any time I try and run make I get the following error.  No matter what source I'm trying to build, I get this same error:

```
make -C /lib/modules/2.6.12-8-386/build SUBDIRS=/home/paper/Desktop/railink/RT25USB-SRC-V2.0.5.0 modules
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-8-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-386'
  CC [M]  /home/paper/Desktop/railink/RT25USB-SRC-V2.0.5.0/rtusb_main.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/paper/Desktop/railink/RT25USB-SRC-V2.0.5.0/rtusb_main.o] Error 127
make[1]: *** [_module_/home/paper/Desktop/railink/RT25USB-SRC-V2.0.5.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-386'
make: *** [all] Error 2

```

The error has to do with the gcc-version.sh file.  How do I fix this?

---

### Post by Zelut on 2005-10-10
have you installed the build-essential package?  $apt-get intall build-essential and that should cover everything you need for manually compiling/building programs.

Otherwise, if you can find the package you want in the repositories I'd suggest installing it via apt-get.

---

### Post by paperdiesel on 2005-10-10
Yes, I have installed it: 

paper@paperdiesel:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paper@paperdiesel:~$

I would much rather get it via a repository, but that won't solve my problem that ANY source I try and build, I get the same error.  What does that error mean?  Has anyone seen it before?

---

### Post by vtechstu on 2005-11-17
Having the same problem, anyone know what is wrong?  Thanks

---


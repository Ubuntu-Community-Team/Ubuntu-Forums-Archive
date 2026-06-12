---
title: "Berkely Logo - Installation Problems"
date: 2006-09-24
forum: Desktop Environments
---

### Post by SilasleCake on 2006-09-24
I have been trying to install Berkely Logo ([http://www.cs.berkeley.edu/~bh/logo.html](http://www.cs.berkeley.edu/~bh/logo.html)) on my laptop but have come across a problem that I am not sure how to fix.

After using the command "./configure" which seems to run fine, I then type "make" which gives me the following message.
```
alejandro@Dell-laptop:~/Desktop/ucblogo$ make
make: *** No rule to make target `xgraphics.o', needed by `logo'.  Stop.

```

If anyone has any idea what I need to do to fix this problem, I would appreciate any help. 

Also, here is what I get after "./configure":
```
alejandro@Dell-laptop:~/Desktop/ucblogo$ ./configure
loading cache ./config.cache
checking for gcc... (cached) gcc
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for POSIXized ISC... no
checking for X... (cached) no
checking for -lm... (cached) yes
checking for -lBSD... (cached) no
checking for -lbsd... (cached) no
checking for -ltermcap... (cached) no
checking for -ltermlib... (cached) no
checking for -lcurses... (cached) no
checking whether cross-compiling... (cached) no
checking for ANSI C header files... (cached) yes
checking for sgtty.h... (cached) yes
checking for termio.h... (cached) yes
checking for unistd.h... (cached) yes
checking for string.h... (cached) yes
checking for size_t... (cached) yes
checking return type of signal handlers... void
checking if signal handlers take argument... yes
checking for usleep... (cached) yes
checking for srandom... (cached) yes
checking for sigvec... (cached) yes
checking for sigsetmask... (cached) yes
checking for matherr... (cached) yes
checking for drem... (cached) yes
checking for irint... (cached) no
checking for bcopy... (cached) yes
checking for memcpy... (cached) yes
checking whether gcc needs -traditional... (cached) no
creating ./config.status
creating makefile
creating config.h
config.h is unchanged

```

---

### Post by SilasleCake on 2006-09-24
The problem has been solved.

---


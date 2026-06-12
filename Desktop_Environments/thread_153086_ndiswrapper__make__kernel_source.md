---
title: "ndiswrapper / make / kernel source?"
date: 2006-03-31
forum: Desktop Environments
---

### Post by Xenom on 2006-03-31
Hello, I have a Links Wireless G (WPC54G) PCMCIA card, now i've downloaded ndiswrapper from sourceforge, i tryed to install it with make, make install, but ndiswrapper is looking for the kernel source.. /lib/modules says : 2.6.12-9-686 

Where do i get the source of the kernel and where do i place it? Can i download it trough Adept? Adept says kernel-source-2.6.11, is this the one i need to install? :-k 

Thanks in advance. 

**This is the message i get**
 Can't find kernel build files in /lib/modules/2.6.12-9-686/build; give the path to kernel build directory with KBUILD=<path> argument to make make[1]: *** [prereq_check] Error 1 make[1]: Leaving directory `/home/xenom/Desktop/ndiswrapper/ndiswrapper-1.11/driver' make: *** [all] Error 2

---

### Post by Xenom on 2006-03-31
Ok, i think ive got ndiswrapper working.

**ndiswrapper -i lsbcmnds.inf**
lsbcmnds is already installed. Use -e to remove it.

:-k I never installed this driver before? Ok, removed it, reinstalled it.

** ndiswrapper -l**
Installed drivers:
lsbcmnds        invalid driver

So, this won't help me mucht either :( Only the power led is burning on my WPC54G Wireless Card.

Anoyone any idea? ](*,)

---


---
title: "Compiling the Kernel"
date: 2009-02-08
forum: General Help
---

### Post by CatmanITA on 2009-02-08
Hello to everyone. I just installed Ubuntu 8.10 on my PC for study reasons and I need to compile a kernel, version 2.6.23. I followed the instructions on the internet and resolved the problems about the "make xconfig" commands, but I cannot resolve a problem with the subsequent instruction "make bzImage".

By reading around I found out that the Gcc I have (version 4.3) cannot compile the kernel.
I found out that I have to modify the makefile (I guess the one I configured before launching make bzImage) as this message says:

Linux 2.6 tree as of this minute doesn't compile with gcc 4.3 trunk. You need
to add -fno-tree-scev-cprop to the KBUILD_CFLAGS, but this is not upstreamed
yet and I am not sure if it'll be accepted in case it results in a performance
regression.
took from [http://gcc.gnu.org/bugzilla/show_bug.cgi?id=32044#c28](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=32044#c28)

I understood I have to add this:
# workaround to avoid gcc 4.3 emitting libgcc calls (see gcc bug #32044)
KBUILD_CFLAGS += $(call cc-option,-fno-tree-scev-cprop,)

but I controlled the makefile and there is already a similar option:
# Force gcc to behave correct even for buggy distributions
CFLAGS          += $(call cc-option, -fno-stack-protector)

so I guess that's not it, or something is wrong. 

The error I get is the following:

kernel/built-in.o: In function `getnstimeofday':
(.text+0x1b29d): undefined reference to `__umoddi3'
kernel/built-in.o: In function `do_gettimeofday':
(.text+0x1b358): undefined reference to `__udivdi3'
kernel/built-in.o: In function `do_gettimeofday':
(.text+0x1b37b): undefined reference to `__umoddi3'
kernel/built-in.o: In function `timekeeping_resume':
timekeeping.c:(.text+0x1b50c): undefined reference to `__udivdi3'
timekeeping.c:(.text+0x1b52f): undefined reference to `__umoddi3'
kernel/built-in.o: In function `update_wall_time':
(.text+0x1bb89): undefined reference to `__udivdi3'
kernel/built-in.o: In function `update_wall_time':
(.text+0x1bbac): undefined reference to `__umoddi3'
kernel/built-in.o: In function `update_wall_time':
(.text+0x1bc43): undefined reference to `__udivdi3'
kernel/built-in.o: In function `update_wall_time':
(.text+0x1bc6d): undefined reference to `__umoddi3'
make: *** [.tmp_vmlinux1] Error 1

Otherwise, I guess I could get an older version of Gcc, but I tried the "force version" option and it didn't work and I don't get how to have the older version working once I get it.


Can anyone help? Thank you!!!

---

### Post by HermanAB on 2009-02-08
if you need to compile a different kernel, not one you want to run on your host, then it is best to do the work inside a Virtual Machine, so that you don't break your host.

So, start by installing Virtualbox or VMware server, then find an old version of ubuntu that has the right version of the kernel and make a VM of that - Bob's your uncle.

Cheers,

Herman

---


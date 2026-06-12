---
title: "Juanty default kernel stack size?"
date: 2009-06-19
forum: General Help
---

### Post by dorkxer on 2009-06-19
What is the default kernel stack size in Ubuntu 9.04?

---

### Post by sdennie on 2009-06-19
```

grep STACK /boot/config-`uname -r`
# CONFIG_4KSTACKS is not set

```

That means it's using the default 8K stacks.

---

### Post by dorkxer on 2009-06-19
If I install a patch to use 16K stacks within my kernel do I still need to build the kernel in order to use the new 16K stacks or does the patch handle all of this?

If the patch handles it all is there a place to download the patches? I have found a few from linuxant, but am wondering if there are other places to get them.

---

### Post by sdennie on 2009-06-19
You would have to recompile the kernel and any external drivers you use (for example, nvidia).  Is there a specific reason you want to change this value?

---

### Post by dorkxer on 2009-06-19
I have a VIA EPIA-SP 8000 and I am trying to get my Netgear WG311v3 PCI wireless card to work. I am using NDISwrapper to load the drivers, but after a minute of the drivers being loaded the machine freezes. 

I have read many forum posts about the subject and done some research, but none of the fixes I have tried seem to resolve the issue. I am not sure if it is the architecture of the board or some low level issue. Some of the forum posts discuss the kernel stack size as a possible issue so I am exploring the possiblity.

---


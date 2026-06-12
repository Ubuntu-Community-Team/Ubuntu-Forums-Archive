---
title: "switching between different kernels?"
date: 2008-12-12
forum: General Help
---

### Post by themusicalduck on 2008-12-12
I was wondering if it's possible to install more than one kernel on an install, so that you can choose which one to use on bootup? For instance installing the RT kernel and the generic kernel, and choosing which one to load at grub or something.

---

### Post by sdennie on 2008-12-12
Yes, it is.  I have 16 different kernels installed at the moment and, other than having a very long list of kernels in grub, it doesn't effect the system in any way.  If you want to have the -rt kernel appear at boot time in grub, I think this will install it properly for you:

```

sudo apt-get install linux-*-rt-*

```

---


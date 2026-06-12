---
title: "trying to compile kernel with PAE support"
date: 2009-06-17
forum: General Help
---

### Post by ittayd on 2009-06-17
Hi,

I have 4GB of memory, and I need PAE support in the kernel to utilize all of it. At first I used the 'server' kernel, but then suspend stopped working, so now I'm trying to compile the kernel myself.

I've followed the instructions for "The Old-Fashioned Debian Way" in [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile), and turned PAE through menuconfig, but when I use `free` I still only see 3GB of RAM.

> cat /boot/config-`uname -r` | grep PAE
CONFIG_X86_PAE=y
> free
             total       used       free     shared    buffers     cached
Mem:       3087736    2007580    1080156          0     210496     794284
-/+ buffers/cache:    1002800    2084936
Swap:      2851496          0    2851496

---

### Post by ittayd on 2009-06-17
i just did the obvious thing and tried to suspend and it doesn't work. X crashes and restarts and after that trying to suspend just locks the screen.

i would appreciate any help. i only changed the PAE configuration in the kernel.

---

### Post by ittayd on 2009-06-17
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=2d4a34c9365c6e3f94a5b26ce296e1fce9b66c8b](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=2d4a34c9365c6e3f94a5b26ce296e1fce9b66c8b)

how can i be sure this commit is in my kernel (2.6.28-9 ?)

---


---
title: "kernel build aftermath"
date: 2006-01-23
forum: Desktop Environments
---

### Post by nwcowboysfan on 2006-01-23
I recently tried to recompile my first kernel which didn't go so well, luckily I was easily able to switch back to using my old, working kernel. However, now I am trying to install the ATI drivers for my laptop which includes doing the following process:

   #in /lib/modules/fglrx/build_mod
    ./make.sh

which returned the following error:

ATI module generator V 2.0
==========================
initializing...
Error:
kernel includes at /usr/src/linux/include do not match current kernel.
they are versioned as "2.6.12-hibernate"
instead of "2.6.12-10-386".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

I am not exactly sure what is going on, uname -r produces 2.6.12-10-386. The only traces of the 2.6.12-hibernate are in /lib/modules which I would also like to get rid of if possible.

Thanks to anyone for help...it case you couldn't tell I am still pretty new to this.

---

### Post by nwcowboysfan on 2006-01-23
Well....on further investigation I have found a bigger problem. When I try to install a newer kernel version it still uses my faulty config file! Can anyone give me some idea as to how to return to the original config? Do we I have to recompile the kernel again?

---


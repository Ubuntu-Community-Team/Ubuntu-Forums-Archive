---
title: "Kernel panic with DSDT"
date: 2006-03-11
forum: Desktop Environments
---

### Post by Okami on 2006-03-11
Hello

I need to boot Ubuntu with a custom DSDT because otherwise Xorg cannot start with "direct rendering" enabled.  

If I read here [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) Ubuntu kernel is already patched for use with custom DSDT, but I get kernel panic which is described further down at that site (Problems with initramfs (2.6 kernels)). However when I try to apply the patch to fix that the kernel stop compiling with an error

init/initramfs.c:502: error: redefinition of 'find_dsdt'
init/initramfs.c:477: error: previous definition of 'find_dsdt' was here
init/initramfs.c:477: varning: 'find_dsdt' defined but not used

I wonder if someone know what to do about this?

Thanks in avance.

Edit: I got it working, with the default Ubuntu kernel. 
Finally everything works, from the beginning not even able to boot Ubuntu  because of bugs in the DSDT which caused problems with the graphic card ati radeon 320m, and now even have direct rendering :)

---


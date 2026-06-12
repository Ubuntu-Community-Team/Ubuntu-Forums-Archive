---
title: "USplash for vanilla kernel"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Firyar on 2006-10-04
Hi everyone,

i compiled a vanilla 2.6.18 kernel and want to use it with the nice usplash splashscreen ubuntu uses. It seems that everything depends on the ramdisk and how the splash screen is inserted in these ramdisk.

The hint to simply use "dpkg-reconfigure linux-image-`uname -r`, or something similar, does not help. Of course there is no such package installed because the kernel was compiled from scratch -- as mentioned above.

Is there anyone who can tell me how to include usplash into the ramdisk of a vanilla kernel? Perhaps only which files so that i can manually build a ramdisk or write a script for this purpose?

---

### Post by xXx 0wn3d xXx on 2006-10-04
Try reinstalling usplash, add a vga resolution option to grub, or make sure your added support for vga graphics and bootup logo.

---

### Post by Firyar on 2006-10-04
> Try reinstalling usplash, 

That does not help. There is nothing wrong with the install of the deb package.

> add a vga resolution option to grub,

I use vga=791 because the resolution best fits for me.

> or make sure your added support for 
> vga graphics and bootup logo.

Also checked this, still no usplash.

---

### Post by christhemonkey on 2006-10-04
See this howto:
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper#HOWTO_use_Usplash_with_your_recompiled_kernel](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper#HOWTO_use_Usplash_with_your_recompiled_kernel)

---


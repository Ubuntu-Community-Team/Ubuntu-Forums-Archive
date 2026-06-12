---
title: "Intrepid stuck on older kernel"
date: 2008-12-09
forum: General Help
---

### Post by Koobi on 2008-12-09
i recently upgraded from 8.04 to 8.10 and lost absolutely all sound.

in an attempt to get it back, i downloaded **alsa-driver-1.0.18a**, unzipped it on my desktop and ran configure:
```

$ sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=via82xx --with-oss=yes

```

i get some weird warnings though:
```

checking for GCC version... ./configure: eval: line 5136: syntax error near unexpected token `)'
./configure: eval: line 5136: `my_compiler_version=4.3.2-1ubuntu11)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
.
.
.
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... yes
cat: /usr/src/linux-headers-2.6.25-2-386/include/linux/kmod.h: No such file or directory
.
.
.
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting

```

the strange thing is that **kmod.h** does exist...but it's a symlink pointing to a file that **doesn't** exist:
```

$ ls -lah /usr/src/linux-headers-2.6.25-2-386/include/linux/kmod.h 
lrwxrwxrwx 1 root root 52 2008-12-09 19:51 /usr/src/linux-headers-2.6.25-2-386/include/linux/kmod.h -> ../../../linux-headers-2.6.25-2/include/linux/kmod.h

```

so it looks like i'm stuck on kernel 2.6.25-2 although 2.6.27 exists:
```

$ uname -r
2.6.25-2-386

```
and yes, i've rebooted many times and the kernel version stays the same.

i believe i can fix the sound issue if i figure this kernel issue out. does anyone have any ideas?

thanks.

---


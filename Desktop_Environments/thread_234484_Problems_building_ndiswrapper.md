---
title: "Problems building ndiswrapper"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Jossie on 2006-08-11
Hi,

To install my Wifi, I need to build the latest ndiswrapper. With the ndiswrapper that I can install using Synaptic, it doesn't work.:( 

So, I installed the Kernel-headers. Also I download the latest ndiswrapper (Ver. 1.22). At the beginning, it starts fine to build :

```

~/Desktop/ndiswrapper-1.22$ sudo make
make -C driver
make[1]: Entering directory `/home/deruyjo1/Desktop/ndiswrapper-1.22/driver'
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/deruyjo1/Desktop/ndiswrapper-1.22/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  LD      /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/built-in.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/hal.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/iw_ndis.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/loader.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/misc_funcs.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/ndis.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/ntoskernel.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/ntoskernel_io.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/pe_linker.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/pnp.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/proc.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/wrapmem.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/wrapndis.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/wrapper.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/usb.o
  CC [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/divdi3.o
  LD [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/ndiswrapper.mod.o
  LD [M]  /home/deruyjo1/Desktop/ndiswrapper-1.22/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: Leaving directory `/home/deruyjo1/Desktop/ndiswrapper-1.22/driver'

```

So far so good ! :)

Then the problems begin ... :(

```

make -C utils
make[1]: Entering directory `/home/deruyjo1/Desktop/ndiswrapper-1.22/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: syntax error before &#8216;size_t&#8217;
../driver/loader.h:24: warning: no semicolon at end of struct or union
../driver/loader.h:26: error: syntax error before &#8216;}&#8217; token
../driver/loader.h:52: error: array type has incomplete element type
../driver/loader.h:56: error: array type has incomplete element type
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: syntax error before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c:95: error: dereferencing pointer to incomplete type
loadndisdriver.c:96: error: dereferencing pointer to incomplete type
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:159: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:162: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:162: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:214: error: storage size of &#8216;driver_file&#8217; isn&#8217;t known
loadndisdriver.c:218: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:218: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:222: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:223: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:225: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:233: error: syntax error before &#8216;struct&#8217;
loadndisdriver.c:214: warning: unused variable &#8216;driver_file&#8217;
loadndisdriver.c:236: warning: control reaches end of non-void function
loadndisdriver.c: At top level:
loadndisdriver.c:237: error: syntax error before &#8216;return&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:251: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:253: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:261: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:263: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:269: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:269: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:273: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:282: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:282: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:284: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:286: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:286: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:284: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:347: error: syntax error before &#8216;struct&#8217;
loadndisdriver.c:349: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:351: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:358: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:364: warning: control reaches end of non-void function
loadndisdriver.c: At top level:
loadndisdriver.c:383: error: syntax error before &#8216;*&#8217; token
loadndisdriver.c: In function &#8216;add_driver_devices&#8217;:
loadndisdriver.c:389: error: &#8216;from&#8217; undeclared (first use in this function)
loadndisdriver.c:390: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:390: error: &#8216;driver_name&#8217; undeclared (first use in this function)
loadndisdriver.c:391: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:391: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:396: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:405: error: dereferencing pointer to incomplete type
loadndisdriver.c:406: error: dereferencing pointer to incomplete type
loadndisdriver.c:409: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:409: error: dereferencing pointer to incomplete type
loadndisdriver.c:410: error: dereferencing pointer to incomplete type
loadndisdriver.c:411: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:415: error: dereferencing pointer to incomplete type
loadndisdriver.c:416: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:421: error: dereferencing pointer to incomplete type
loadndisdriver.c:421: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:425: error: &#8216;devices&#8217; undeclared (first use in this function)
loadndisdriver.c:427: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:448: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:450: error: dereferencing pointer to incomplete type
loadndisdriver.c:452: warning: implicit declaration of function &#8216;strncat&#8217;
loadndisdriver.c:452: warning: incompatible implicit declaration of built-in function &#8216;strncat&#8217;
loadndisdriver.c:411: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_all_devices&#8217;:
loadndisdriver.c:472: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:474: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:474: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:474: error: &#8216;driver&#8217; undeclared (first use in this function)
loadndisdriver.c:474: warning: left-hand operand of comma expression has no effect
loadndisdriver.c:474: warning: statement with no effect
loadndisdriver.c:480: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:480: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:480: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:482: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:484: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:490: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:496: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:497: error: dereferencing pointer to incomplete type
loadndisdriver.c:498: error: dereferencing pointer to incomplete type
loadndisdriver.c:501: error: dereferencing pointer to incomplete type
loadndisdriver.c:502: warning: implicit declaration of function &#8216;S_ISDIR&#8217;
loadndisdriver.c:504: error: dereferencing pointer to incomplete type
loadndisdriver.c:505: error: dereferencing pointer to incomplete type
loadndisdriver.c:509: error: dereferencing pointer to incomplete type
loadndisdriver.c:510: error: dereferencing pointer to incomplete type
loadndisdriver.c:515: error: dereferencing pointer to incomplete type
loadndisdriver.c:531: error: syntax error before &#8216;struct&#8217;
loadndisdriver.c:472: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:552: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:552: error: &#8216;proc_misc&#8217; undeclared (first use in this function)loadndisdriver.c:560: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:560: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:561: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:561: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:571: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:571: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:576: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:577: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:577: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:577: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:579: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:584: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:605: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:605: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:605: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:605: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:605: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)loadndisdriver.c:607: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:609: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:611: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:611: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:621: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:636: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:668: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/deruyjo1/Desktop/ndiswrapper-1.22/utils'
make: *** [all] Error 2

```

:(

Somebody an idea why this happens ? What do I need more ??

---

### Post by mlind on 2006-08-11
Do you have linux-headers package for your kernel installed?

Very easy way to build ndiswrapper is to use **module-assistant** package.
(btw. don't use sudo when invoking make)

```

sudo aptitude install module-assistant
m-a prepare
m-a get ndiswrapper-source
m-a build ndiswrapper-source

```

Or just 
```

m-a auto-install ndiswrapper-source

```

You probably need to use sudo with these commands if you don't belong to **src** group.

---

### Post by Jossie on 2006-08-11
I'm sorry ...

The kernel-headers are installed
I just installed module-assisant, but it won't work :( How do I point to the package that I downloaded ?

I realy like to install with 'make', because I read in several posts that it is the only way to be sure to get the ndiswrapper CORRECT installed.

---

### Post by mlind on 2006-08-11
> **Jossie said:**
> I'm sorry ...

The kernel-headers are installed
I just installed module-assisant, but it won't work :( How do I point to the package that I downloaded ?

I realy like to install with 'make', because I read in several posts that it is the only way to be sure to get the ndiswrapper CORRECT installed.

module-assistant is just for compiling the kernel module, but you can do it the way you want. I just tested this with m-a, and it worked.

kernel-headers package is different than **linux-headers**..
Try
```

sudo aptitude install linux-headers-$(uname -r)

```

---

### Post by Jossie on 2006-08-12
> **mlind said:**
> 

kernel-headers package is different than **linux-headers**..
Try
```

sudo aptitude install linux-headers-$(uname -r)

```

I did what you asked, but it seems everything is correctly installed

```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

Building the ndiswrapper driver seems not to be the problem. The problem is (I guess) building the ndiswrapper-utils. Maybe I just have to download something more, but I don't know what...

---

### Post by mlind on 2006-08-12
You have installed build-essential package right? Those missing headers are either provided by **libc6-dev** or **linux-kernel-headers** which build-essential also installs.

---

### Post by Jossie on 2006-08-12
When I check my Synapthic Package Manager panel: yes **build-essential** is installed. (Version 11.1)

---

### Post by mlind on 2006-08-12
> **Jossie said:**
> When I check my Synapthic Package Manager panel: yes **build-essential** is installed. (Version 11.1)

Do you have /usr/src/linux symlink pointing to installed kernel headers ? If you also have libc6-dev and linux-kernel-headers installed, then I dunno why make process fails.

---

### Post by Jossie on 2006-08-12
**libc6-dev** and **linux-kernel-headers** are installed .. :(

---

### Post by mlind on 2006-08-12
> **Jossie said:**
> **libc6-dev** and **linux-kernel-headers** are installed .. :(

What about /usr/src/linux symlink?

---

### Post by Jossie on 2006-08-12
I don't have a file (or folder) named **symlink** under **/usr/src/linux**

---

### Post by mlind on 2006-08-12
> **Jossie said:**
> I don't have a file (or folder) named **symlink** under **/usr/src/linux**

No, I mean create symbolic link, **/usr/src/linux**, which points to installed kernel headers on /usr/src.

```

ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux

```

You may need to use sudo if you're not on **src** group. Go into /usr/src folder and make sure that linux symlink points to correct kernel headers.

---

### Post by Jossie on 2006-08-12
That 's it ! :):)

ndiswrapper is succesfully installed, the driver also. Finally I see my WlanO in my network list.

I can start another chapter : configuering it to my secured network ...

Many thanks for your time to help a newby like me. If you come over to Belgium once, I pay you a beer.

---

### Post by mlind on 2006-08-12
> **Jossie said:**
> That 's it ! :):)

ndiswrapper is succesfully installed, the driver also. Finally I see my WlanO in my network list.

I can start another chapter : configuering it to my secured network ...

Many thanks for your time to help a newby like me. If you come over to Belgium once, I pay you a beer.

Thanks for the offer :mrgreen: 
Glad you got it working in the end.

---


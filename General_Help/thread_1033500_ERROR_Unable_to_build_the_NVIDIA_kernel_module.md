---
title: "ERROR: Unable to build the NVIDIA kernel module"
date: 2009-01-07
forum: General Help
---

### Post by PoopyTheJ on 2009-01-07
I've just installed Intrepid on a machine at work, we use a rather large database and without using hardware acceleration scrolling through the database entries takes forever. The machine we are using has an Nvidia Vanta video card on it and looking through the list of supported cards it's on there but intrepid doesn't prompt me to use restricted drivers. So I went to nvidia's site to get the package downloaded got the build-essentials, kernel-source, headers and gcc installed but when running the installer it errors out. I'm attaching the log file below anyone have any ideas?

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jan  7 12:18:14 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 71.86.06.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-11-gener
   ic/build SYSOUT=/lib/modules/2.6.27-11-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-11-generic/build SUBDIRS
   =/tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -i
   nclude include/linux/autoconf.h
    -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-str
   ict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march
   =i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronou
   s-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mac
   h-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling
   -calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz7655
   /NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -W
   switch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multich
   ar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAME
   S -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNE
   L__ -DMODULE -DNV_VERSION_STRING=\"71.86.06\" -DNV_UNIX -DNV_LINUX -DNV_INT6
   4_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nv)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz7655/NVIDIA-Linux-x86-71
   .86.06-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-p
   kg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1975: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:83,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:104:27:
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:106,
                    from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h: In fun
   ction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:595: er
   ror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   ‘__nv_setup_pat_entries’:
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:887: warning:
   comparison between signed and unsigned
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   ‘__nv_restore_pat_entries’:
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:913: warning:
   comparison between signed and unsigned
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1239: warning
   : comparison between signed and unsigned
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1242: error: 
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1246: warning
   : comparison between signed and unsigned
   /tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1249: error: 
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz7655/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by PoopyTheJ on 2009-01-08
Is Intrepid just not going to use the nvidia driver? I know some people have gotten the nvidia driver to work, and I've tried a number of different avenues but nothing worked. I'm assuming this has something to do with the whole xen kernel thing but I don;t really know what that means. Anyone have any ideas?

---

### Post by PoopyTheJ on 2009-01-24
Ok, tried Nouveau and just get a black screen. NV driver though installed doesn't appear to do anything exact same performance with nv in my xorg as without. Sooooooo, what can I do, there's gotta be a driver that will work with this Vanta.

---

### Post by dcstar on 2009-01-24
> **PoopyTheJ said:**
> Ok, tried Nouveau and just get a black screen. NV driver though installed doesn't appear to do anything exact same performance with nv in my xorg as without. Sooooooo, what can I do, there's gotta be a driver that will work with this Vanta.

AFAIK 8.10 does not support the older NVIDIA cards, and I believe that will be in the kernel.

You can try the Envy scripts (envy-core package) as they detect, download and install Nvidia drivers for you.

---

### Post by sepia-shots on 2009-01-25
How do you use the envyng-core scripts? I have an nvidia 8500GT which whilst I can use the latest driver, fails to boot with a response requiring a rebuild of the config (which fails). The only success I have is in allowing the machine to run in basic graphics mode.

---

### Post by PoopyTheJ on 2009-01-27
figured it was an 8.10 issue so I went ahead and reinstalled using 8.04, now though I'm limited to 800x600 at 60Hz, which I wasn't when using the Vesa driver.

---

### Post by PoopyTheJ on 2009-01-27
sepia-shots look for the envyng-core scripts in Synaptic, or I assume that ```
sudo apt-get install envyng-core
``` would work

---


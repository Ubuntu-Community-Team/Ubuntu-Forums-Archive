---
title: "Ubuntu 8.04 Tweak"
date: 2009-02-28
forum: General Help
---

### Post by gsgentry on 2009-02-28
I just installed Ubuntu 8.04 and am still very new to all of this, but I am trying. Anyway, does anyone know how I can get it to show an "X" in the top right of a program window so I can close it from there instead of right clicking and choosing close from the taskbar?

Thank you for the help!!

---

### Post by Iowan on 2009-02-28
Which program? Most of the programs on this Gutsy box (haven't checked them all) have the three buttons (Min, Max, Close) in the upper right corner.

---

### Post by gsgentry on 2009-02-28
Any program... I purchased a Dell Mini 9 with Ubuntu and anything that I open has a X to close the window but when I installed Ubuntu on my desktop, I do not see that X. Now I did load Maximus Netbook Remix on both machines as well but one has it and one doesn't.

It is like I am missing the entire top title bar and buttons on everything.

---

### Post by lswb on 2009-02-28
Are you using compiz? Try this command from a terminal:
gtk-window-decorator --replace &

In a normal compiz installation this command will run automatically at startup. If it restores the normal windows for you we will need to figure out what is wrong with your installation.

---

### Post by gsgentry on 2009-02-28
It was an original install and compiz was on there but I removed it hoping that it would restore the title bars but no luck.

---

### Post by NoReflex on 2009-02-28
I did have the same problem as you on Ubuntu Hardy. What I did was to leave compiz enabled and install simple compiz settings manager (sudo apt-get install simple-ccsm).
Then I opened System -> Preferences -> Compiz Settings Manager and in the Effects tab unckeck and recheck Window Decoration and this made the titlebar visible.

Best wishes,
NoReflex

---

### Post by gsgentry on 2009-03-01
I have already tried that too and it didn't help.

I have read that there is an issue with NVIDIA cards so I followed the directions on correcting that by downloading and compiling the NVIDIA-Linux-x86-180.08-pkg1.run driver. I went through that and then received a libc header error... corrected that by downloading the libc development package and now I am getting the error "Unable to load the kernel module nvidia.ko. I am not sure how to get around this to fix it.

On another note, I un-installed my original NVIDIA driver and played with a few things. Well this time when I loaded Firefox to post this message, I saw the title bar and buttons for a second, then they went away. :(

Here is my installer log...


```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Feb 28 14:54:12 2009
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA GeForce FX 5900XT GPU installed in this system is supported
         through the NVIDIA 173.14.xx legacy Linux graphics drivers.  Please
         visit http://www.nvidia.com/object/unix.html for more information. 
         The 180.08 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 180.08 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 180.08.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-23-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-23-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-23-gener
   ic/build SYSOUT=/lib/modules/2.6.24-23-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-23-generic/build SUBDIRS
   =/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  
   -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototyp
   es -Wno-trigraphs -fno-strict-aliasing
    -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -m
   regparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtu
   ne=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mac
   h-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-
   statement -Wno-pointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1
   /usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\
   "180.08\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD
   _BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6412
   /NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-18
   0.08-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pk
   g1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-
   struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffre
   estanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit
   -frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-p
   ointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wal
   l -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses
   -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -
   Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBU
   G -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6412/NVIDIA-
   Linux-x86-180.08-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D_
   _KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retu
   rn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -
   maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-poin
   ter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign
     -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_D
   EBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__
   KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred
   -stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-ou
   tgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-s
   tack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tmp/self
   gz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -DNDEBUG  -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-180
   .08-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.
   08-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g
    -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/t
   mp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -
   Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-
   x86-180.08-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6412/NVIDIA-Linux-x86-18
   0.08-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=gener
   ic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-defaul
   t -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statemen
   t -Wno-pointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08
   \" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/sel
   fgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz641
   2/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/s
   rc/nv/nv-kernel.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv
   .o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/os-agp.o /tmp/selfgz6412/NVID
   IA-Linux-x86-180.08-pkg1/usr/src/nv/os-interface.o /tmp/selfgz6412/NVIDIA-Li
   nux-x86-180.08-pkg1/usr/src/nv/os-registry.o /tmp/selfgz6412/NVIDIA-Linux-x8
   6-180.08-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pk
   g1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-23-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-23-generic/Modu
   le.symvers -I /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/Module
   .symvers -o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/Module.s
   ymvers -w  -s
   WARNING: could not find /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__K
   ERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_M
   ODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-1
   80.08-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-p
   kg1/usr/src/nv/nv
   idia.mod.c
     ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz6412/NVIDIA-Linux-
   x86-180.08-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6412/NVIDIA-Linux-x86-180.08
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/s
   rc/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   37.184006] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1
   across:1502036k
   [   37.732748] EXT3 FS on sda1, internal journal
   [   37.839080] device-mapper: uevent: version 1.0.3
   [   37.839107] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised:
   dm-devel@redhat.com
   [   39.000944] ip_tables: (C) 2000-2006 Netfilter Core Team
   [   39.326502] No dock devices found.
   [   39.599708] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+
   processors (1 cpu cores) (version 2.20.00)
   [   39.599732] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND,
   Evaluating _PSS [20070126]
   [   39.606883] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
   [   39.638668] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND,
   Evaluating _PSS [20070126]
   [   40.213760] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
   [   40.213765] apm: overridden by ACPI.nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Feb 28 14:54:12 2009
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA GeForce FX 5900XT GPU installed in this system is supported
         through the NVIDIA 173.14.xx legacy Linux graphics drivers.  Please
         visit http://www.nvidia.com/object/unix.html for more information. 
         The 180.08 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 180.08 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 180.08.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-23-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-23-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-23-gener
   ic/build SYSOUT=/lib/modules/2.6.24-23-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-23-generic/build SUBDIRS
   =/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  
   -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototyp
   es -Wno-trigraphs -fno-strict-aliasing
    -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -m
   regparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtu
   ne=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mac
   h-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-
   statement -Wno-pointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1
   /usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\
   "180.08\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD
   _BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6412
   /NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-18
   0.08-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pk
   g1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-
   struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffre
   estanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit
   -frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-p
   ointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wal
   l -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses
   -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -
   Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBU
   G -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6412/NVIDIA-
   Linux-x86-180.08-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D_
   _KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retu
   rn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -
   maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-poin
   ter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign
     -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_D
   EBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__
   KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred
   -stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-ou
   tgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-s
   tack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tmp/self
   gz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -DNDEBUG  -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-180
   .08-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.
   08-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g
    -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/t
   mp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -
   Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-
   x86-180.08-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6412/NVIDIA-Linux-x86-18
   0.08-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=gener
   ic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-defaul
   t -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statemen
   t -Wno-pointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08
   \" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/sel
   fgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz641
   2/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/s
   rc/nv/nv-kernel.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv
   .o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/os-agp.o /tmp/selfgz6412/NVID
   IA-Linux-x86-180.08-pkg1/usr/src/nv/os-interface.o /tmp/selfgz6412/NVIDIA-Li
   nux-x86-180.08-pkg1/usr/src/nv/os-registry.o /tmp/selfgz6412/NVIDIA-Linux-x8
   6-180.08-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pk
   g1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-23-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-23-generic/Modu
   le.symvers -I /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/Module
   .symvers -o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/Module.s
   ymvers -w  -s
   WARNING: could not find /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__K
   ERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_M
   ODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-1
   80.08-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-p
   kg1/usr/src/nv/nv
   idia.mod.c
     ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz6412/NVIDIA-Linux-
   x86-180.08-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6412/NVIDIA-Linux-x86-180.08
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/s
   rc/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   37.184006] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1
   across:1502036k
   [   37.732748] EXT3 FS on sda1, internal journal
   [   37.839080] device-mapper: uevent: version 1.0.3
   [   37.839107] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised:
   dm-devel@redhat.com
   [   39.000944] ip_tables: (C) 2000-2006 Netfilter Core Team
   [   39.326502] No dock devices found.
   [   39.599708] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+
   processors (1 cpu cores) (version 2.20.00)
   [   39.599732] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND,
   Evaluating _PSS [20070126]
   [   39.606883] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
   [   39.638668] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND,
   Evaluating _PSS [20070126]
   [   40.213760] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
   [   40.213765] apm: overridden by ACPI.
   [   40.314918] ppdev: user-space parallel port driver
   [   40.396380] audit(1235850810.347:2): type=1503
   operation="inode_permission" requested_mask="a::" denied_mask="a::"
   name="/dev/tty" pid=5369 profile="/usr/sbin/cupsd" namespace="default"
   [   44.792914] NET: Registered protocol family 17
   [   47.437800] NET: Registered protocol family 10
   [   47.437994] lo: Disabled Privacy Extensions
   [   58.274332] eth0: no IPv6 routers present
   [  106.702156] nvidia: module license 'NVIDIA' taints kernel.
   [  106.707923] NVRM: The NVIDIA GeForce FX 5900XT GPU installed in this
   system is
   [  106.707926] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers.
   Please
   [  106.707927] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [  106.707928] NVRM:  information.  The 180.08 NVIDIA driver will ignore
   [  106.707930] NVRM:  this GPU.  Continuing probe...
   [  106.708529] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
   [   40.314918] ppdev: user-space parallel port driver
   [   40.396380] audit(1235850810.347:2): type=1503
   operation="inode_permission" requested_mask="a::" denied_mask="a::"
   name="/dev/tty" pid=5369 profile="/usr/sbin/cupsd" namespace="default"
   [   44.792914] NET: Registered protocol family 17
   [   47.437800] NET: Registered protocol family 10
   [   47.437994] lo: Disabled Privacy Extensions
   [   58.274332] eth0: no IPv6 routers present
   [  106.702156] nvidia: module license 'NVIDIA' taints kernel.
   [  106.707923] NVRM: The NVIDIA GeForce FX 5900XT GPU installed in this
   system is
   [  106.707926] NVRM:  supported through the NVIDIA 173.14.xx Legacy nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Feb 28 14:54:12 2009
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA GeForce FX 5900XT GPU installed in this system is supported
         through the NVIDIA 173.14.xx legacy Linux graphics drivers.  Please
         visit http://www.nvidia.com/object/unix.html for more information. 
         The 180.08 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 180.08 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 180.08.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-23-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-23-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-23-gener
   ic/build SYSOUT=/lib/modules/2.6.24-23-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-23-generic/build SUBDIRS
   =/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL__  
   -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototyp
   es -Wno-trigraphs -fno-strict-aliasing
    -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -m
   regparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtu
   ne=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mac
   h-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-
   statement -Wno-pointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1
   /usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\
   "180.08\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD
   _BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6412
   /NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-18
   0.08-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pk
   g1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-
   struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffre
   estanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit
   -frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-p
   ointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wal
   l -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses
   -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -
   Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBU
   G -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6412/NVIDIA-
   Linux-x86-180.08-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D_
   _KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retu
   rn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -
   maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-poin
   ter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign
     -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_D
   EBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz6412/N
   VIDIA-Linux-x86-180.08-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__
   KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred
   -stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-ou
   tgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-s
   tack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tmp/self
   gz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -DNDEBUG  -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-180
   .08-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.
   08-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g
    -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/t
   mp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -
   Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6412/NVIDIA-Linux-
   x86-180.08-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6412/NVIDIA-Linux-x86-18
   0.08-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=gener
   ic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-defaul
   t -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statemen
   t -Wno-pointer-sign   -I/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.08
   \" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/sel
   fgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz641
   2/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/s
   rc/nv/nv-kernel.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv
   .o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/os-agp.o /tmp/selfgz6412/NVID
   IA-Linux-x86-180.08-pkg1/usr/src/nv/os-interface.o /tmp/selfgz6412/NVIDIA-Li
   nux-x86-180.08-pkg1/usr/src/nv/os-registry.o /tmp/selfgz6412/NVIDIA-Linux-x8
   6-180.08-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pk
   g1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-23-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-23-generic/Modu
   le.symvers -I /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/Module
   .symvers -o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/Module.s
   ymvers -w  -s
   WARNING: could not find /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__K
   ERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_M
   ODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz6412/NVIDIA-Linux-x86-1
   80.08-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-p
   kg1/usr/src/nv/nv
   idia.mod.c
     ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz6412/NVIDIA-Linux-
   x86-180.08-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6412/NVIDIA-Linux-x86-180.08
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6412/NVIDIA-Linux-x86-180.08-pkg1/usr/s
   rc/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   37.184006] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1
   across:1502036k
   [   37.732748] EXT3 FS on sda1, internal journal
   [   37.839080] device-mapper: uevent: version 1.0.3
   [   37.839107] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised:
   dm-devel@redhat.com
   [   39.000944] ip_tables: (C) 2000-2006 Netfilter Core Team
   [   39.326502] No dock devices found.
   [   39.599708] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+
   processors (1 cpu cores) (version 2.20.00)
   [   39.599732] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND,
   Evaluating _PSS [20070126]
   [   39.606883] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
   [   39.638668] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND,
   Evaluating _PSS [20070126]
   [   40.213760] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
   [   40.213765] apm: overridden by ACPI.
   [   40.314918] ppdev: user-space parallel port driver
   [   40.396380] audit(1235850810.347:2): type=1503
   operation="inode_permission" requested_mask="a::" denied_mask="a::"
   name="/dev/tty" pid=5369 profile="/usr/sbin/cupsd" namespace="default"
   [   44.792914] NET: Registered protocol family 17
   [   47.437800] NET: Registered protocol family 10
   [   47.437994] lo: Disabled Privacy Extensions
   [   58.274332] eth0: no IPv6 routers present
   [  106.702156] nvidia: module license 'NVIDIA' taints kernel.
   [  106.707923] NVRM: The NVIDIA GeForce FX 5900XT GPU installed in this
   system is
   [  106.707926] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers.
   Please
   [  106.707927] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [  106.707928] NVRM:  information.  The 180.08 NVIDIA driver will ignore
   [  106.707930] NVRM:  this GPU.  Continuing probe...
   [  106.708529] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.drivers.
   Please
   [  106.707927] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [  106.707928] NVRM:  information.  The 180.08 NVIDIA driver will ignore
   [  106.707930] NVRM:  this GPU.  Continuing probe...
   [  106.708529] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by 3rdalbum on 2009-03-01
If your desktop has Maximus, then remove it. Part of Maximus' job is to remove the title bars! If that's not the problem, then try running this command:

```
metacity --replace
```

That will turn off Compiz until you reboot and use the "old" window manager. Metacity is boring but it will always give you title bars (as long as you're not running Maximus).

---

### Post by gsgentry on 2009-03-01
I have Maximus running on my netbook and the title bars are fine.

Anyway... I will give that a try. Will removing Maximus change the way my desktop looks now? I really like the look and would prefer to keep it if possible.

---

### Post by gsgentry on 2009-03-01
OK... I unchecked Maximus in the Sessions and rebooted. It appears to be working now but is still slow because I removed all of the NVIDIA Drivers including the one that came up when I initially installed Ubuntu. I am going to try to figure out how to get Ubuntu to detect this again so I can reload them. If anyone has any ideas, feel free to shout.

Thanks for the help!!

---


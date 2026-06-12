---
title: "VMware"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Gadgeteer on 2006-08-13
I installed it off of synaptic and went to configure it when I got this error:

[I]None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?[/I]

So, I say yes...and it says/asks this:

[I]Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel?[/I]

how can I find out where my header files are?

---

### Post by vijirajan on 2006-08-13
You have to install it.

```

sudo apt-get install linux-headers-`uname -r`

```

---

### Post by Gadgeteer on 2006-08-13
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-26-386/build/include]

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in
the "/tmp/vmware-config0" directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.




this is what happens when I try after the install.

---

### Post by simonn on 2006-08-13
What does the following return?

```

$ ls -l /lib/modules/2.6.15-26-386/build

```

If there are no errors above, what does the following return?

```

$ ls -l /lib/modules/2.6.15-26-386/build/include

```

---

### Post by Gadgeteer on 2006-08-13
arch
block
cluster
crypto
drivers
fs
include
init
ipc
kernel
lib
Makefile
mm
Module.symvers
net
scripts
security
sound
usr




and


total 28
lrwxrwxrwx   1 root root    42 2006-08-13 20:26 acpi -> ../../linux-headers-2.6.15-26/include/acpi
lrwxrwxrwx   1 root root     8 2006-08-13 20:26 asm -> asm-i386
lrwxrwxrwx   1 root root    47 2006-08-13 20:26 asm-alpha -> ../../linux-headers-2.6.15-26/include/asm-alpha
lrwxrwxrwx   1 root root    45 2006-08-13 20:26 asm-arm -> ../../linux-headers-2.6.15-26/include/asm-arm
lrwxrwxrwx   1 root root    47 2006-08-13 20:26 asm-arm26 -> ../../linux-headers-2.6.15-26/include/asm-arm26
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-cris -> ../../linux-headers-2.6.15-26/include/asm-cris
lrwxrwxrwx   1 root root    45 2006-08-13 20:26 asm-frv -> ../../linux-headers-2.6.15-26/include/asm-frv
lrwxrwxrwx   1 root root    49 2006-08-13 20:26 asm-generic -> ../../linux-headers-2.6.15-26/include/asm-generic
lrwxrwxrwx   1 root root    47 2006-08-13 20:26 asm-h8300 -> ../../linux-headers-2.6.15-26/include/asm-h8300
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-i386 -> ../../linux-headers-2.6.15-26/include/asm-i386
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-ia64 -> ../../linux-headers-2.6.15-26/include/asm-ia64
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-m32r -> ../../linux-headers-2.6.15-26/include/asm-m32r
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-m68k -> ../../linux-headers-2.6.15-26/include/asm-m68k
lrwxrwxrwx   1 root root    51 2006-08-13 20:26 asm-m68knommu -> ../../linux-headers-2.6.15-26/include/asm-m68knommu
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-mips -> ../../linux-headers-2.6.15-26/include/asm-mips
lrwxrwxrwx   1 root root    48 2006-08-13 20:26 asm-parisc -> ../../linux-headers-2.6.15-26/include/asm-parisc
lrwxrwxrwx   1 root root    49 2006-08-13 20:26 asm-powerpc -> ../../linux-headers-2.6.15-26/include/asm-powerpc
lrwxrwxrwx   1 root root    45 2006-08-13 20:26 asm-ppc -> ../../linux-headers-2.6.15-26/include/asm-ppc
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-s390 -> ../../linux-headers-2.6.15-26/include/asm-s390
lrwxrwxrwx   1 root root    44 2006-08-13 20:26 asm-sh -> ../../linux-headers-2.6.15-26/include/asm-sh
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-sh64 -> ../../linux-headers-2.6.15-26/include/asm-sh64
lrwxrwxrwx   1 root root    47 2006-08-13 20:26 asm-sparc -> ../../linux-headers-2.6.15-26/include/asm-sparc
lrwxrwxrwx   1 root root    49 2006-08-13 20:26 asm-sparc64 -> ../../linux-headers-2.6.15-26/include/asm-sparc64
lrwxrwxrwx   1 root root    44 2006-08-13 20:26 asm-um -> ../../linux-headers-2.6.15-26/include/asm-um
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 asm-v850 -> ../../linux-headers-2.6.15-26/include/asm-v850
lrwxrwxrwx   1 root root    48 2006-08-13 20:26 asm-x86_64 -> ../../linux-headers-2.6.15-26/include/asm-x86_64
lrwxrwxrwx   1 root root    48 2006-08-13 20:26 asm-xtensa -> ../../linux-headers-2.6.15-26/include/asm-xtensa
lrwxrwxrwx   1 root root    45 2006-08-13 20:26 cluster -> ../../linux-headers-2.6.15-26/include/cluster
drwxr-xr-x 542 root root 12288 2006-08-13 20:26 config
lrwxrwxrwx   1 root root    42 2006-08-13 20:26 keys -> ../../linux-headers-2.6.15-26/include/keys
drwxr-xr-x   2 root root 16384 2006-08-13 20:26 linux
lrwxrwxrwx   1 root root    46 2006-08-13 20:26 math-emu -> ../../linux-headers-2.6.15-26/include/math-emu
lrwxrwxrwx   1 root root    43 2006-08-13 20:26 media -> ../../linux-headers-2.6.15-26/include/media
lrwxrwxrwx   1 root root    41 2006-08-13 20:26 mtd -> ../../linux-headers-2.6.15-26/include/mtd
lrwxrwxrwx   1 root root    41 2006-08-13 20:26 net -> ../../linux-headers-2.6.15-26/include/net
lrwxrwxrwx   1 root root    44 2006-08-13 20:26 pcmcia -> ../../linux-headers-2.6.15-26/include/pcmcia
lrwxrwxrwx   1 root root    44 2006-08-13 20:26 prism2 -> ../../linux-headers-2.6.15-26/include/prism2
lrwxrwxrwx   1 root root    42 2006-08-13 20:26 rdma -> ../../linux-headers-2.6.15-26/include/rdma
lrwxrwxrwx   1 root root    43 2006-08-13 20:26 rxrpc -> ../../linux-headers-2.6.15-26/include/rxrpc
lrwxrwxrwx   1 root root    42 2006-08-13 20:26 scsi -> ../../linux-headers-2.6.15-26/include/scsi
lrwxrwxrwx   1 root root    43 2006-08-13 20:26 sound -> ../../linux-headers-2.6.15-26/include/sound
lrwxrwxrwx   1 root root    43 2006-08-13 20:26 video -> ../../linux-headers-2.6.15-26/include/video
lrwxrwxrwx   1 root root    42 2006-08-13 20:26 wlan -> ../../linux-headers-2.6.15-26/include/wlan

---

### Post by simonn on 2006-08-13
What about:

```

$ls -l /usr/lib/vmware-player/modules/source/vmmon.tar

```

---

### Post by Gadgeteer on 2006-08-14
no such file or directory

---

### Post by iamhugeinjapan on 2006-08-14
Are you following instructions or working it out on your own?

These instructions are quite helpful
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)
or alternative angle:
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

The installation process is mostly just accepting all default answers to the questions the installer asks. You do need the kernel headers and a compiler installed though - as detailed in the instructions.

---

### Post by Gadgeteer on 2006-08-14
Would I need the managment interface? It sounds like just changing settings over the net...which I wouldn't be doing.

---

### Post by iamhugeinjapan on 2006-08-14
That's up to you. Default answers to the questions should get you up and running at least.

---


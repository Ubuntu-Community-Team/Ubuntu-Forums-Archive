---
title: "Kernel Compilation"
date: 2008-12-11
forum: General Help
---

### Post by godsownman on 2008-12-11
Hello Everyone: 

Firstly, I'm not sure if this is the right place for this question, but, I didn't find another suitable place. Sorry If I'm in the wrong place.

Secondly, I'm a newbie to ubuntu.

Now my problem,

Im working on Ubuntu 8.04. I need to re-compile the kernel from the default 8.04 kernel (2.6.24...) to (2.6.17.1 ). The reason Im doing this is to use the L7 Filter which has difficulties working on kernels post 2.6.19 or so. 

I've been googling around to find the steps to recompile the kernel and I followed them, but I keep getting some errors. The latest one reads : 

> 
init/built-in.o: In function `try_name':
/usr/src/linux-2.6.17.1/init/do_mounts.c:115: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
/usr/src/linux-2.6.17.1/init/do_mounts.c:206: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
/usr/src/linux-2.6.17.1/init/do_mounts.c:363: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
/usr/src/linux-2.6.17.1/init/do_mounts.c:321: undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
/usr/src/linux-2.6.17.1/init/initramfs.c:206: undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:/usr/src/linux-2.6.17.1/arch/i386/kernel/ptrace.c:634: more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.1'
make: *** [debian/stamp-build-kernel] Error 2
root@abc-desktop:/usr/src/linux-2.6.17.1# 




Ive used the following commands : 

> 

cd /usr/src
tar xvjf linux-source*
cd linux-source
cp /boot/config-2.x.x.x.x .config
sudo make menuconfig

cofigure the heck out of your kernel

sudo make-kpkg --initrd --append-to-version=mykerne1 kernel_image kernel_headers

cd ..
sudo dpkg -i linux-image-2.6.10*.deb




I, however, haven't been able to use  the last line as yet ! :confused: .

I've got gcc version : " gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)"


Please help me out with this. Thanks a lot!

---

### Post by blazemore on 2008-12-11
There's an application that will download the latest kernel, apply the latest patch, runs the config tool, automatically compiles it and adds it to grub
it's called KernelCheck and its thread is here [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)

---

### Post by godsownman on 2008-12-11
Thanks for all the help, however, my situation is a little different.

I do not want the latest kernel,  instead I want an earlier one.

---

### Post by godsownman on 2008-12-11
Help!!

---

### Post by godsownman on 2008-12-13
Have I posted this in the wrong section, why isn't anyone replying?

---

### Post by master_kernel on 2008-12-23
It seems to me that you are either missing dependencies, you have selected some bad configuration options, or that this specific kernel has some issues with Ubuntu. Is there any chance you can compile the latest patched version of the 2.6.18 kernel?

---


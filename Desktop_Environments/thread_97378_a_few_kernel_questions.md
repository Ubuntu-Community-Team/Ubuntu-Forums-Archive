---
title: "a few kernel questions"
date: 2005-11-30
forum: Desktop Environments
---

### Post by MButterman on 2005-11-30
I'm enjoying the posts for compiling kernels and was successful with my first one but have a few questions.

1. one option to compiling a kernel is multi-processor support. While I understand this to mean physical number of them but would this option include support for the hyperthreading Pentium 4. (Prescott)?

2. While these articles deal with compiling with 386 kernels, would it be better for me to upgrade the kernel to 686 then compile the kernel? 

3. Is there a guide explaining what the modules do or support? With my next compile I would like to remove the un-needed ones. I have been gathering from different posts  that by trimming down the kernel to only what it requires then it tends to offer  better performance.

1.My idea is to use synaptic to upgrade the kernel to 686 then delete the 386 one.

2.then recompile it using the latest stable kernel.

Any suggestions to do this would be welcomed and appreciated. TY for all the great posts and ideas

AMB,
MButterman

---

### Post by RAOF on 2005-11-30
1) I believe that SMP support is for both having multiple CPUs and also Hyperthreading

2) You will be compiling your kernel for whatever specific CPU you have - if you have a P4 you will actually be compiling a -P4 kernel (one of the first options in the kernel configuration is what CPU you have).  The source is the same for all the kernels - 386,686,k7, even amd64 & PPC

3) Removing **modules** will do nothing but free up some (in the order of 10s of MB) disc space.  That's one of the points of modules - if you don't need it, it doesn't get loaded and so there's no performace increase (except that it will take slightly less time to compile your kernel) from excluding unneeded modules.  If you **really** know what you're doing, you can build things into the kernel and not use modules at all.  **That** is faster, but it's really not worth the effort.  When I compile my kernels, I build **every possible** module.  It takes longer to compile, and ends up being ~50MB of modules, but it means that if I add some hardware, or plug something into a usb port, or whatever I won't need to rebuild anything, 'cause the drivers are already there :)

---

### Post by MButterman on 2005-12-01
I have actually done the "Compiling Kernels For Newbies" and while this far removes me from expert. I have interest in compiling them.  I was interested in compiling with  the recent stable kernel. There is a HOW-TO that has been posted for it. TY for the input and would like to hear how you compile yours.

AMB,
MButterman

---

### Post by az on 2005-12-01
[QUOTE=MButterman]I'm enjoying the posts for compiling kernels and was successful with my first one but have a few questions.

1. one option to compiling a kernel is multi-processor support. While I understand this to mean physical number of them but would this option include support for the hyperthreading Pentium 4. (Prescott)?

2. While these articles deal with compiling with 386 kernels, would it be better for me to upgrade the kernel to 686 then compile the kernel? 

3. Is there a guide explaining what the modules do or support? With my next compile I would like to remove the un-needed ones. I have been gathering from different posts  that by trimming down the kernel to only what it requires then it tends to offer  better performance.

1.My idea is to use synaptic to upgrade the kernel to 686 then delete the 386 one.

2.then recompile it using the latest stable kernel.

Any suggestions to do this would be welcomed and appreciated. TY for all the great posts and ideas

AMB,
MButterman[/QUOTE]

1. Yes.

2.  Your compile will take less time if you are running a 686 kernel, since it is optimised and everything will go a little faster.  The built kernel will not be any different whether you are running a 386 or 686 kernel.  You can even cross-compile a smp-686 kernel from a mac or something.

3. Look in the Documentation folder in the kernel tree (Use the Source, Luke)


1.  Yes.  Good.  The easies way to custom-build a kernel is to use kernel-package.  You make your new kernel into a package and then install it.  You can then remove it and the package scripts prevent you from having a non-booting system.

2.  kernel-package works fine with the latest source from Linus.

install kernel-package, build-essential and gcc3.4

config your kernel (Your running config is in /boot)
sudo make-kpkg --initrd --revision=1 --append-to-version=mycusomkernel --stem=linux kernel_image kernel_headers


You should use fakeroot instead of sudo, but whatever....

---

### Post by MButterman on 2005-12-02
TY for the great information but what is fakeroot and how is that installed and used? I successfully recompiled a 686 kernel and use it. Although it was difficult at first, I now am aware of the process. As a side note, I'm glad I made the switch to Ubuntu, it has been quite the learning process but It's been a gratifying one. :D 

AMB,
MButterman

---


---
title: "This makes no freaking sense! Can't install Kernel?"
date: 2006-05-06
forum: Desktop Environments
---

### Post by raid517 on 2006-05-06
Hi I compiled a kernel on Ubuntu Debian in the normal way:

make-kpkg clean && make-kpkg --initrd --revision=custom.1.0 kernel_image

However after the kernel had compiled without errors and I had navigated to the upper level directory containing my new kernel and try to install it using 

dpkg -i kernel-2.6-16.deb I get a complaint that the kernel-2.6-16.deb already exists - which is just a standard warning as I had already compiled a previous version of this kernel (although I hadn't used it yet - as I had to go back and add some modules I had missed). The message warned me that if I went ahead and installed in that directory that this might cause me some problems. So I quit the install/dpkg process and renamed the folder to kernel-2.6.16.old and then I ran dpkg -i kernel-2.6-16.deb again. However this time I got another error message saying 'error can't find directory /lib/modules/kernel-2.6.16.' The process then dies and refuses to continue. So I get an error whether the /lib/modules/kernel-2.6.16 directory is present or whether it isn't. It's a totally nonsensical condition.


I also get an error message when trying to install that says can't locate module dm.mod - which as it appears to be the device mapper module would seem to be quite important. (Although I'm still not quite clear what it is?)

It may or may not be significant - but I am trying to compile and install a 2.6.16 kernel on a system that is currently running a recent 2.4x kernel version. It is much too complicated and irrelevant to go into detail on why I am running a 2.4x kernel, execpt to say that this really is currently my only option). I have (I think) all of the required tools installed - so the question is what on earth is going on?

If I create an empty directory (since this is what dpkg appears to expect to find) at /lib/modules/linux-2.6.12 the kernel will install - but there is no modules created in the /lib/modules/linux-2.6.12 folder.

Obviously I must still be missing some important stuff - but the question is what? And why would the kernel compile cleanly if I was missing some files/modules that dpkg expects to find?

GJ

---

### Post by ranf on 2006-05-07
I always used the "--append-to-version" parameter with make-kpkg.

---


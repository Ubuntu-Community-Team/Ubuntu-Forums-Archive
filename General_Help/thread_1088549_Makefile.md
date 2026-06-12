---
title: "Makefile"
date: 2009-03-06
forum: General Help
---

### Post by jordanguyoflove on 2009-03-06
hi,

[I] buil a new kernel and now I have to add a .c file to the Makefile.
I don't know what the makefile is.
Anyone help thanks.[/I]

---

### Post by beno1990 on 2009-03-06
The Makefile is the file the build manager (make) reads through to see what files need to be compiled and how.

What C file are you trying to add to the kernel? You need to be more specific about what you're trying to do.

---

### Post by jordanguyoflove on 2009-03-06
Hey man thanks for the reply I appreciate it.
Well I have a helloworld.c file. 

> #include <linux/linkage.h>
#include <linux/kernel.h>
asmlinkage int sys_helloworld() {
 printk(KERN_EMERG "hello world!");

return 1;
}

I am trying to add a new system call ( a bit useless but it's for my assignment). My book is very vague and tells me: Add your file helloworld.c to the Makefile(if you created a new file for your system call)... Youu can now build the new kernel.

previously I added .long sys_helloworld to the sys_call_table
and
defined a new system call number for _NR_helloworld in unistd.h

---

### Post by beno1990 on 2009-03-06
Well firstly, put the source file in the ./kernel/ directory under the kernel source's root dir (in other words, assuming the kernel source is at /usr/src/linux, put it inside the /usr/src/linux/kernel)

then edit the Makefile in the same directory.

Add helloworld.o after sched_clock.o in the obj-y block (on the same line).

Add obj-y += helloworld.o after obj-$(CONFIG_SMP) += sched_cpupri.o (on a new line)

---

### Post by jordanguyoflove on 2009-03-06
Thanks a lot man.
It really helped.


I got one more question.
How do I build my kernel now?

Previously I built it using these commands:

> make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Then

> dpkg -i linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb


Should I do the same thing now that I modified the kernel by adding a system call?

Thanks.
from [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)

---

### Post by beno1990 on 2009-03-06
You'd need to be root to do any of those commands successfully, so you should have used sudo -s or sudo -i beforehand

Also, before the commands you have there, you should copy your kernel configuration over with this command:

```

cp /boot/config-$(uname -r) .config && yes "" | make oldconfig

```

Other than that, those are the right commands for building your kernel.

---

### Post by jordanguyoflove on 2009-03-06
I can't thank you enough you saved me.

---


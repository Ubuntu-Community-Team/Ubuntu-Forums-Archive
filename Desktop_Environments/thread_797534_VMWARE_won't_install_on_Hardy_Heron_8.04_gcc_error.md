---
title: "VMWARE won't install on Hardy Heron 8.04 gcc error"
date: 2008-05-17
forum: Desktop Environments
---

### Post by paulstaf on 2008-05-17
During the configuration script, I get hung up at this question:

*************************************
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.24-16-generic/build/include

The directory of kernel headers (version 2.6.24.3) does not match your running 
kernel (version 2.6.24-16-generic).  Even if the module were to compile 
successfully, it would not load into the running kernel.
***********************************************

No matter what path I type in there I get the same thing.  I have read and read and read and patched and patched and still cannot get past this.

I have a Dell Dimension E521 AMD64 running the 32 bit version of Hardy.

I really need to have VMWARE running and don't want to go back to Gutsy.
This was a fresh install of Hardy.

Thank you in advance....

---

### Post by hoarycripple on 2008-05-17
I have VMware workstation running fine on hardy.  

Do you have the kernel headers installed?

Also, what happens if you specify your include path as:

/usr/src/linux-headers-2.6.24.16-generic/include

---

### Post by paulstaf on 2008-05-17
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24.16-generic/include

The path "/usr/src/linux-headers-2.6.24.16-generic/include" is not an existing 
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

I have installed all the linux header files I have found to install.

Thanks,
Paul

---


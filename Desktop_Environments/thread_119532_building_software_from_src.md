---
title: "building software from src"
date: 2006-01-19
forum: Desktop Environments
---

### Post by wbh1 on 2006-01-19
Hi all, 

I just started using ubuntu a few days ago.  I've been avoiding this problem till now, but I need the ability to compile and install the kernel and modules from source.

I have a tv capture card that is not supported by the default kernel.  I need to compile a module, and for that, I'm assuming I'll need the kernel src, along with your standard programming tools.  I know I'm going to need build-essentials, and perl, but is there anything else you think I might need?  Build essentials includes kernel headers but wouldn't I need the kernel src?  Any suggestions you have are welcome.

Eventually, I would love to be able to make my ubuntu install compile oddball programs as easily as it once was on slackware.

---

### Post by az on 2006-01-19
[QUOTE=wbh1]  I need to compile a module, and for that, I'm assuming I'll need the kernel src, along with your standard programming tools.  I know I'm going to need build-essentials, and perl, but is there anything else you think I might need?  Build essentials includes kernel headers but wouldn't I need the kernel src? ...

Eventually, I would love to be able to make my ubuntu install compile oddball programs as easily as it once was on slackware.[/QUOTE]


Build essential brings in what was formerly known as libc6-dev.  That package was split up to accomodate for non-linux kernels (BSD, Hurd) into libc6-dev and linux-kernel-headers; It is basically the dev interface for libc to the kernel.  The linux kernel source headers are what you need to compile kernel modules.

So, you need to install build-essential and linux-headers-(version which matches your kernel)

An oversight in Breezy is that the kernel was not buildable with gcc-4.0, the compiler used in everything else.  Build essential does not depend on it - you need to install it yourself.

gcc-3.4


Ex:  
sudo apt-get install build-essential linux-headers-2.6.12-10-686 gcc-3.4

With that, you are good to go to compile kernel modules.  You do not need the full linux source, if your source package is properly made.

To compile other stuff, you need to install any developmental headres that are relevant to what you need to compile.  Like xlibs-dev of libgtk2.0-dev, for example.  Read the readme in the tarball and search for a corresponding "-dev" package.

---


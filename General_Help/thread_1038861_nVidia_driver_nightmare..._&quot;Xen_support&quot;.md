---
title: "nVidia driver nightmare... &quot;Xen support&quot; conflict"
date: 2009-01-14
forum: General Help
---

### Post by greylander on 2009-01-14
Hope someone can help.  Can't seem to install nVidia drivers of any sort.

I have a fresh install of 8.10, 64 bit.  Running on an HP Pavillion dv9000 (dv9334us to be exact).  

If I boot to console and and install driver downloaded from nvidia.com, as with command:

   sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run

it first finds no precompiled kernel interface... then fails to find one for download... then attempts to compile... and *then* says I have a "Xen kernel" and I need to use a kernel without "Xen support".  But this is the plain 8.10 distribution.

I've already found a couple related bug reports for this:
   [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224340](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224340)
   [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290888](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290888)

They make clear the problem, but not the workaround (if any).

What is my best option to work around this problem?  Would it be fairly easy to recompile the kernel without "Xen support"?  (I'm highly technical, but new to Linux).  Or should I download and install a version that lacks this "Xen support"?

You might ask why I'm going with the proprietary drivers.  Already could not get the non-proprietary ones to work... which I'll ask about in a separate thread.  I think I may end up needing the proprietary drivers anyway, because I want to hook my laptop up to an external monitor.

Thanks for any help!

---


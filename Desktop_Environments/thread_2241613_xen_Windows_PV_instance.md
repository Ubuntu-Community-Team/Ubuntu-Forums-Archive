---
title: "xen Windows PV instance"
date: 2014-08-27
forum: Desktop Environments
---

### Post by mike194 on 2014-08-27
Good day everyone!

I just installed a fresh copy of 14.04 and installed the xen hypervisor and everything works as expected.  However, upon various sites, I found that Windows actually should be installed as a HVM.  By some sort of black magic, I was able to install it as a PV.

I'm fairly new to xen so I'm still reading the documentation but so far, it looks like this really isn't supported.  Is there a reason for that?  From what I've read, Xen PV is really more for Linux guests and if you want to use non-linux guests, they should be installed via HVM.

Both installs went well and I'm trying to determine what is the best type of guest to keep.  My sense is that the HVM performance will be more of that like a physical machine but the host machine may suffer as a result whereas a PV machine be at the mercy of the hypervisor.

I'm personally leaning toward keeping the PV since performance is not to much of an issue with me.

Thoughts?

---


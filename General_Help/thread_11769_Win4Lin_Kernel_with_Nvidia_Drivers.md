---
title: "Win4Lin Kernel with Nvidia Drivers"
date: 2005-01-19
forum: General Help
---

### Post by sgbeamer on 2005-01-19
I'm having trouble compiling the Nvidia kernel driver in my win4lin custom 2.6.8.1 kernel.  I have a working kernel using the ubuntu sources and the win4lin patches as described elsewhere in the forum but I can't get the Nvidia driver to compile.   I tried the nvidia installer and it looks like it's working but X crashes on startup.  It looks like the module is bad from the logs.   I tried the ubuntu sources for the nvidia driver and had no luck there either.

Has anybody else worked through this?  Any suggestions?   Thanks - Steve

Further investigation reveals that the Nvidia installer installs a later version than the Ubuntu driver so there is a version mismatch between the glx driver in XFree and the kernel module.  I will see if I can sort this out.

Final revision - I was able to sort this out.  The kernel is good so if anybody needs a win4lin kernel let me know.  The latest Nvidia package is 6629 which I installed on the win4lin kernel and the warty release has deb packages for the 6111 Nvidia driver.  I removed the 6629 drivers, went to the archive on the Nvidia website and installed the 6111 drivers.  Now both kernels work equally well.  Problem solved.

---


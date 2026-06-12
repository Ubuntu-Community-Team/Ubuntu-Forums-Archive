---
title: "Install 180.27 .run on 2 kernels?"
date: 2009-02-08
forum: General Help
---

### Post by ThunderRd on 2009-02-08
I haven't seen this topic covered, so maybe someone can point me in the right direction.

On a clean Xubuntu 8.10/64 installation I have successfully installed the current nvidia driver from this file: NVIDIA-Linux-x86_64-180.27-pkg2.run

I have since built a custom kernel which I plan to use as my everyday kernel, keeping the original kernel as a failsafe.  When I booted to the new kernel I got low-res mode.  I was not surprised, because I expected to have to install the nvidia driver to each kernel in order to build the modules for each one.

After shutting down gdm I attempted to install on the new kernel, but nvidia-installer wants to remove the previous install, which means that it will successfully install to kernel 2, and remove itself from kernel 1.  This is not a deal-breaker, but it would be nice to be able to have it properly working on both kernels.  I have studied the documentation but can't seem to find any hints on what to do, like a command argument to not touch the other kernel.

Is there a way to do this?

---

### Post by ThunderRd on 2009-02-09
If I'm in the wrong forum please let me know.  I didn't really know where this belonged.

---

### Post by johnjohn2 on 2009-02-09
> **ThunderRd said:**
> If I'm in the wrong forum please let me know.  I didn't really know where this belonged.

just start the new kernel DKMS should take care of the rest

---

### Post by ThunderRd on 2009-02-10
> **johnjohn2 said:**
> just start the new kernel DKMS should take care of the rest

I thought that would be the case; but when I booted into the other kernel it did not install and dropped to low-res.

As I said, it isn't a major problem but if it were working properly it would be nice.

---

### Post by Ng Oon-Ee on 2009-02-11
DKMS won't work with the NVidia binary, unfortunately. I'm sure there's some hacker-ish way to make it work, but I'd recommend you choose a kernel and stick to it. I tried this as well, previously, but never found a solution.

---

### Post by ThunderRd on 2009-02-11
By the binary I take it you mean the .run method with the integrated script.

Would dkms work with the other package?

---


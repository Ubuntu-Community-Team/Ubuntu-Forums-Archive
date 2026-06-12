---
title: "wine errors re:nvidia driver mismatch"
date: 2007-11-02
forum: Desktop Environments
---

### Post by bturrie on 2007-11-02
I was having stability problems with my gutsy system so I bailed and reinstalled feisty. I have a core 2 duo machine with a an nvidia 7300le pcie video card. i'm using the proprierary nvidia-glx drivers (nvidia-glx-new would not work at all). Anyway when i try running winefile I'm getting some messages about a video driver mismatch. here are some examples. 

Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but
this client has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but
this client has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.


Winefile ran but clearly theres a problem, If I had to guess I'd say that the nvidia-kernel modules found by adept don't match the nvidia-glx driver. of course the nvidia-glx-new drivers would not run and I don't see any other kernel modules. any suggestions? 

I considered installing "envy" but decided to post this first.

---

### Post by bturrie on 2007-11-02
i uninstalled nvidia-glx and reinstalled nvidia-glx-new this time it worked fine. no clue why

---


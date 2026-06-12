---
title: "problem with Ubuntu Studio LL Kernel and nVidea"
date: 2007-05-12
forum: Desktop Environments
---

### Post by Pocadotty on 2007-05-12
I just Upgraded to Ubuntu Studio.  When I first booted the machine, Xserver crashed.

I was able to start things without a problem using the Standard Ubuntu Kernel, so all is not lost...

I want to use the Ubuntu Studio low latency kernel for music creation. but I need to install a kernel module for my nVidea card. can someone please tell me how to do this....

Thanks

---

### Post by MetalMusicAddict on 2007-05-12
> **Pocadotty said:**
> I just Upgraded to Ubuntu Studio.  When I first booted the machine, Xserver crashed.

I was able to start things without a problem using the Standard Ubuntu Kernel, so all is not lost...

I want to use the Ubuntu Studio low latency kernel for music creation. but I need to install a kernel module for my nVidea card. can someone please tell me how to do this....

Thanks

Boot into the -generic kernel. Install **linux-lowlatency** and you should be fine.

---

### Post by Pocadotty on 2007-05-12
I did, and it works great!

Thanks metalmusicadict

---


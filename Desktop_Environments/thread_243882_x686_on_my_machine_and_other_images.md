---
title: "x686 on my machine and other images"
date: 2006-08-25
forum: Desktop Environments
---

### Post by spyke01 on 2006-08-25
i saw that using the x686 image will increase performance, so i downloaded it and tried booting into it, and the x server crashes. however when i booted back into my 386 everythings fine. My processor is a celeron, could this cause the xserver to crash? 

the other question is can i remove all the older 386 images ie those below 26?

---

### Post by orb9220 on 2006-08-25
Yep you can remove the older kernals thru synaptic. On reboot they should  not be listed.

I see people having problems with the 686.

---

### Post by az on 2006-08-25
You forgot to install the restricted modules for your new kernel.

Install the linux-686 package instead of the linux-image-686 package.  The linux-686 package depends on everything including the corresponding linux-restricted-modules package) you need and not just the kernel image.

There's nothing wrong with the 686 kernel, just some bad advice as to how to install it.

---

### Post by orb9220 on 2006-08-25
Sorry It might have been the 64-bit kernels that were having problems.

Still learning.

---

### Post by spyke01 on 2006-08-25
thanks guys installing linux-686 worked great thanks a ton guys

---


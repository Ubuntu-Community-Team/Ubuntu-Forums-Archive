---
title: "Restricted modules in update"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Toet on 2006-07-12
I've noticed that with the update today, a new kernel version was being installed. With the 386 version of the kernel, the restricted modules are included. 
I'm using the k7 version, and this kernel was also updated with the update. But the k7 restricted modules were not included in the update. I have to add them myself with synaptic. From previous experience I know that if I do not install the restricted modules, my X won't start anymore cause of the nvidia drivers. Then I have to reboot into my old kernel and install the restricted modules manually.

Does anyone know if there is a reason why the restricted modules are not in the update? And if there is not a good reason, where should I drop the wish to include it in the future?

---

### Post by mcduck on 2006-07-12
when you installed the K7 kernel, did you install 'linux-k7' package or did you just pick the kernel version you wanted? linux-k7 is a metapackage that depends on the latest kernel image, restricted modules, kernel headers etc.. So as long as you have that installed you should also get all updates for your kernel..

---

### Post by Toet on 2006-07-12
Whoops and thanks.

---

### Post by llamakc on 2006-07-12
Double thanks from me also.

---


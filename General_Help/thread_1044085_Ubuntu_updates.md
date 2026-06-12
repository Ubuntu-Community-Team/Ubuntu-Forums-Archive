---
title: "Ubuntu updates"
date: 2009-01-19
forum: General Help
---

### Post by sodaforce on 2009-01-19
Hi all,

I have recently installed Ubuntu 8.10 and installed the updates as advised by the package manager. When i come to the grub boot menu it lists Linux-kernel-2.xx.x as it did before but also there is now another newer Linux-kernel entry.

Firstly i was wondering why another kernel has been installed along side the previous one and not just overwritten it? I'm imagining that its so i can test stuff still works, and it does beautifully. Secondly as everything is working should i remove it and how would i do such a thing?

Thanks.

---

### Post by Pidgin on 2009-01-19
I think you can leave it. The old kernels are kept in case that the new kernel fails.

---

### Post by plucky on 2009-01-19
> Firstly i was wondering why another kernel has been installed along side the previous one and not just overwritten it? 


This will happen when ever there is a kernel update and it is for the reason you specify > I'm imagining that its so i can test stuff still works, and it does beautifully.

> Secondly as everything is working should i remove it and how would i do such a thing?

I would keep at least one older kernel ,just in case you break the current kernel,then you can boot the older version to fix the problem.

If you still want to remove the older kernel,open **Synaptic Package Manager** and search for **linux-image** and mark for complete removal.Please make sure you have selected the correct kernel and not the current kernel as that would break your system.


Good Luck.

---

### Post by adamlau on 2009-01-19
Unless you have a purposefully small /boot partition, you are advised to retain at least one previous kernel for fallback purposes. If you insist on removing associated /boot/grub/menu.list entries, you may either comment them out (suggested) or remove them outright. The initial ramdisk and compressed kernel files are found in /boot. Proceed with caution, remove old files if you wish (I do :)).

---

### Post by sodaforce on 2009-01-19
Thanks for all your replies. On your general advice i will keep the current set up and remove old kernels as they are replaced. 

Thanks again.

---


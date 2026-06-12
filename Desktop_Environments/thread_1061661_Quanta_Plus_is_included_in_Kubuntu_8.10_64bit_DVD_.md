---
title: "Quanta Plus is included in Kubuntu 8.10 64bit DVD Version , desktop edition ?"
date: 2009-02-06
forum: Desktop Environments
---

### Post by lse123 on 2009-02-06
**Quanta Plus(Latest)** is included in Kubuntu 8.10 64bit DVD Version , desktop edition ? If I make a USB STICK bootable with this DVD it will also included in the USB ?

---

### Post by warp99 on 2009-02-06
> **lse123 said:**
> **Quanta Plus(Latest)** is included in Kubuntu 8.10 64bit DVD Version , desktop edition ? If I make a USB STICK bootable with this DVD it will also included in the USB ?

If you use the USB creator included with Ubuntu 8.10 you can create a persistent mode and then install Quanta from the repositories like you normally would.

Now with persistent mode you can update the entire OS if you like except the kernel through the package manager, but be warned the persistent mode takes ** a lot of space** since it keeps the original files and the updated files in a seperate file called casper-rw. The only packages I would absolutely not update is the kernel since it breaks some dependencies.

Also with persistent mode for some unknown reason the system log files in /var/log may become very large, mine were over 300 MB, for no apparent reason and will have to be emptied. Also anytime you boot to a different machine in persistent mode any network settings, device settings, and udev rules will also be saved. 

This is fine if you only use the USB drive on one or two machine, but if you use the same drive on multiple machines it could become a problem. I solved this with some custom scripts that empties the mtab file, restores original udev rules, and empties all network settings and log files on shutdown. If you're interested I would be happy to post these with a short howto.

---

### Post by maybeway36 on 2009-02-06
It would also be possible (but complicated) to unpack the filesystem.squashfs from the DVD, add Quanta Plus, then repack it.

---


---
title: "inux-686/ linux-generic/ linux-image-generic/ linux-image-2.6.27-7-virtual/ etc"
date: 2008-12-09
forum: General Help
---

### Post by lardandweed on 2008-12-09
Could somebody fill me in on what the differences between them are? 

like... what's the difference between-
linux-686 (or linux-k7, etc) and linux-generic
linux-generic and linux-image-generic

and so on...

---

### Post by werries on 2008-12-09
linux-686 and k7 were made for newer Intel and AMD processors, specifically.

Linux-generic is the kernel configured for general public use, with standard options. The linux-image is a package in addition, that contains a bunch of files for the kernel. (im not entirely sure what.) And the virtual kernel is made without all the drivers that are unnecessary for use in a virtual machine, (such as VMware)

---

### Post by lardandweed on 2008-12-09
ic. So you can't have linux-image-generic installed without the linux-generic right? It's kinda like windows and service packs? Pardon me if i have to use a sort of warped analogy. haha

then what's the difference between linux-generic and linux-2.6.27-7-generic?

---

### Post by albinootje on 2008-12-09
linux-image-generic is a meta-package just like linux-image-server.

If you would want the kernel which is installed by default from the Ubuntu server install cdrom, then sudo apt-get install linux-image-server would be enough to install linux-image-2.6.27-9-server on Ubuntu Intrepid Ibex.

---

### Post by lardandweed on 2008-12-09
i r confused! haha! so from what i gather ...

generic = standard installation
server = server installation

linux-generic = installs the latest standard kernel revision
linux-x.x.x.x-generic = installs the specified standard kernel revision

linux-image-generic = linux-generic + some extra files?

> **albinootje said:**
> If you would want the kernel which is installed by default from the Ubuntu server install cdrom, then sudo apt-get install linux-image-server would be enough to install linux-image-2.6.27-9-server on Ubuntu Intrepid Ibex.

 hmm, to clarify things, why would one choose for example linux-image-generic over linux-generic?

---


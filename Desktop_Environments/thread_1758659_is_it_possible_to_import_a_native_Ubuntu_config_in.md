---
title: "is it possible to import a native Ubuntu config into VirtualBox"
date: 2011-05-14
forum: Desktop Environments
---

### Post by RBLevin on 2011-05-14
I will be taking delivery of a new laptop in a week or so. I want to set up several VMs under VirtualBox. Host OS will be the native Windows install that comes with the PC.

I have two laptops I use now, both booting Ubuntu 11.04. I would like to import these configs into a VirtualBox VDI, and them move the VMs over to the new PC.

Googling this has turned up many good threads that relate to importing a native Windows config into VBox or importing VMware VMs into VBox, but I have yet to find a thread that documents importing a native Ubuntu config into VBox.

Wondering if this can be done and if anyone can point me to a good tutorial.

Of course, I will hit the VirtualBox forums with this query as well, and will cross-post any solutions I find.

THANKS.

---

### Post by 67GTA on 2011-05-15
You could try remastersys to make a backup iso of your existing Ubuntu install, and then use it to install in Virtualbox. Remastersys will clone your hard drive install and the live cd/dvd backup can be burned to disc and then used as an install disc. It is also useful for just making a fully installable backup of your Ubuntu OS. [http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

---

### Post by RBLevin on 2011-05-15
> **67GTA said:**
> You could try remastersys to make a backup iso of your existing Ubuntu install, and then use it to install in Virtualbox. Remastersys will clone your hard drive install and the live cd/dvd backup can be burned to disc and then used as an install disc. It is also useful for just making a fully installable backup of your Ubuntu OS. [http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

That's a really cool idea. Thanks. Will look into that.

---


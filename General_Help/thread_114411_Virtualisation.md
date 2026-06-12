---
title: "Virtualisation"
date: 2006-01-08
forum: General Help
---

### Post by Adam Atlas on 2006-01-08
I'm looking for a good virtualisation environment. Specifically, I am looking for one that will run on Ubuntu as a host system, but *not* a "paravirtualisation" system like Xen where it runs another instance of the same kernel directly, but rather, one where the guest system runs in a full virtual machine using a boot disk image. However, I'd like one that can run this at near-native speeds, using a kernel module in the host system if necessary. I'd prefer a open source/free software program to do this, but I would consider a proprietary program as long as it's free as in beer. What would you recommend?

---

### Post by lamego on 2006-01-08
The only open source machine virtualization command which i know is QEMU:
[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)
However the performance of QEMU is really bad compared to the host system.

If you only need this VM software for tests and development you can use the free vmware player.
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
Please note that you will need the demo vmware workstation product to create the virtual machines, then you can just play them for free.
There is also a tool to create VM machines for vmware player, VMXBuilder:
[http://petruska.stardock.net/software/VMware/](http://petruska.stardock.net/software/VMware/)

I have tried a few other virtualization software, my experience is that VMWARE is the one perfoming best.

Hope this helps

---

### Post by Adam Atlas on 2006-01-08
Thanks for the information.

By the way, I should mention that some of my uses for this will be to protect sensitive information in an encrypted virtual machine. That is, I'd have the hard drive image encrypted, and the virtualisation program would have to prompt for the key when starting up, keep the key in memory (I have encrypted swap of course), and dynamically decrypt the image as needed. It would never expose anything in the guest system to the host system, or vice versa, except through authenticated means like SSHing into the guest system from the host. It seems qemu has this capability, but I was hoping there exists a system with better performance. Of course, if anyone can think of a way to achieve this goal (a whole encrypted isolated environment) without using a virtual machine, that would be welcome too.

Thanks.

---

### Post by hentaidan on 2006-01-08
As lamego said, I would say VMware Player is the best regards speed, though does not natively support changing any (emulated) hardware paramaters, unless you want to pay for your beer.

Qemu is good, and very customizable, and with the accelerator module is supposedly as good as other commerical alternatives (I havent tried it myself)

Bochs is also an option for running other OS's, but is very slow compared to the VMware Player. (Bochs is also open-source).

I personally use Qemu because of its speed (over bochs) and customization, though I rarely run any demanding (i.e. Ubuntu) OS for longer than 30min.

---


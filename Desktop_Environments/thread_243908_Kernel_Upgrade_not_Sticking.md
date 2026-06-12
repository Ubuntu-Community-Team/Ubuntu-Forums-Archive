---
title: "Kernel Upgrade not Sticking"
date: 2006-08-25
forum: Desktop Environments
---

### Post by forkbeard on 2006-08-25
I've recently installed Dapper on my MacBook Pro. Most everything went fine but I'm trying to do a kernel upgrade to the latest i686-smp version from the 386 version but it refuses to stick. 

686-smp installs without a hitch but after a reboot, uname -r still shows up as 2.6.15-26-386

Is there anything I've got to do beyond the apt-get install?

[Edit] Just in case you're wondering, I did the apt-get install linux-686-smp not just the image install.

---

### Post by catlett on 2006-08-25
It should work. There are a couple of things to look at. Grub has to list it on the menu and it has to be chosen to boot into that kernel. Check boot and look for the kernel (i.e. vmlinuz and initrd) Then open the grub folder and make sure the entry is in the menu.
Update grub in case it is there but grub missed the installation.
```
sudo update-grub
```

Then go to synaptic package manager and search for 686 kernel. Make sure linux-686-smp is selected. That is the full kernel image. You should also have libc6-i686, linux-image-686, and linux-headers.

If it still isn't working, try removing it and reinstalling with synaptic package manager

---

### Post by Ramses de Norre on 2006-08-25
On dapper there are no smp packages nomore, the smp support is enabled by default in the i686 and k7 kernels and used when needed. In the i386 this option is disabled and thus it's not possible to use more then one core with an i386 kernel..
So I'd install the i686 or k7 kernel (intel or amd) and smp should work then.

---

### Post by forkbeard on 2006-08-25
Since this is all on a MacBook Pro, I'm forced to use lilo. Is there a similar command to update it?

@Ramses: I already installed all the i686 packages, the problem is that Ubuntu keeps booting with the 386 packages. I've tried removing and re-installing the 686 packages as well as removing the 386 packages (all except the running image package, didn't want to risk borking anything) but nothing has worked so far :-\

---

### Post by angkor on 2006-09-07
Lilo needs to be re-run after you make changes to it. Grub does this automatically.

try running lilo and reboot

```
sudo lilo
```

---


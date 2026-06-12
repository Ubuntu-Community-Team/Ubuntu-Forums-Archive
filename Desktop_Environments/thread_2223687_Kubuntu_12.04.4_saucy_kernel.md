---
title: "Kubuntu 12.04.4 saucy kernel"
date: 2014-05-12
forum: Desktop Environments
---

### Post by wallacegalloway on 2014-05-12
Why doesnt Kubuntu 12.04.4 include the saucy kernel like Ubuntu 12.04.4?  I would like to install Kubuntu 12.04 on my ASrock z87 Pro 4 but it won't pick up my network card.

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)

---

### Post by Frogs Hair on 2014-05-12
12.04 is a LTS release and will include kernel updates and upgrades though out it's life. There may be  earlier versions of the iso are available at the link and you would have to freeze the kernel version with potential security risk.  [http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/)

---

### Post by deadflowr on 2014-05-12
> **Frogs Hair said:**
> 12.04 is a LTS release and will include kernel updates and upgrades though out it's life. There may be  earlier versions of the iso are available at the link and you would have to freeze the kernel version with potential security risk.  [http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/)

Kernels on LTS releases, somewhat explained
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by wallacegalloway on 2014-05-12
hmmm...how do I "sudo apt-get install linux-generic-lts-saucy" without  an internet connection? Are the kernels located on the DVD? Point  releases are generally more stable and I like a few of the older  versions of certain applications, as such I prefer 12.04.4.

---

### Post by monkeybrain20122 on 2014-05-12
You just grab the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
You can get any one you want, even newer ones than Saucy's (provided it works of course)

There are 3 packages to download
linux-headers i386/amd64 (i386 or amd64 depending on whether you have 32 or 64 bit OS)
linux-headers all
linux-image i386/amd64

Download all of them to one folder, say Downloads/kernel
then in the terminal
```
cd Downloads/kernel
sudo dpkg -i *.deb
```

Edited: well of course you would need internet connection to download the kernel. But you can download these with another machine and transfer to your system with a usb and then install.

---

### Post by deadflowr on 2014-05-12
> **wallacegalloway said:**
> hmmm...how do I "sudo apt-get install linux-generic-lts-saucy" without  an internet connection? Are the kernels located on the DVD? Point  releases are generally more stable and I like a few of the older  versions of certain applications, as such I prefer 12.04.4.

The saucy series kernel is what is on the version for 12.04.4.
So no need to download it.

as the raring series kernel is on 12.04.3 and and quantal series kernel is on 12.04.2.
The precise series kernel is on 12.04, and 12.04.1.

As per my link before, the quantal,raring, and saucy series kernels will only be supported until 12.04.5 comes, at which point those three will be upgraded to the trusty series kernel, which they will have until precise hits end of life.

The precise series kernel is supported the whole length of life.

What's the out for
```
uname -a 
```

that should give you an idea of which kernel you have
3.2.0-XX-generic = precise
3.5.0-XX-generic = quantal
3.8.0-XX-generic = raring
3.11.0-XX-generic = saucy

FWIW

---

### Post by Frogs Hair on 2014-05-12
> Why _doesnt_ Kubuntu 12.04.4 include the saucy kernel Woops! ;)

---

### Post by wallacegalloway on 2014-05-12
> **deadflowr said:**
> The saucy series kernel is what is on the version for 12.04.4.
So no need to download it.


Unfortuantely this is only true for Ubuntu 12.04.4..not the other derivatives (i.e. Kubuntu)

---

### Post by deadflowr on 2014-05-13
> **wallacegalloway said:**
> Unfortuantely this is only true for Ubuntu 12.04.4..not the other derivatives (i.e. Kubuntu)

I notice their release notes are all wrong
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Kubuntu)
:confused:

---

### Post by wallacegalloway on 2014-05-13
Thanks Monkeybrain..this should do the trick!

---


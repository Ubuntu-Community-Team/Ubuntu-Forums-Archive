---
title: "Sun Virtualbox OS Installation"
date: 2009-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by truing on 2009-11-14
I am a senior(!) beginner with some limited UNIX experience from many years ago. I am running the upgraded version 9.10 of UBUNTU.

I had installed Virtualbox before going on holiday to visit my son and hoping my guru would be able to help with the setup. Too much work and his upcoming marriage understandably(!) left me with no help. I am trying to get XP installed in a virtual machine. I have set my permissions in Vbox user and I have a valid XP disk from my old Dell. Problem is how do I actually install the OS? It appears from searching around help files that I need an ISO version of the disk or am I leading myself astray?

The error screen when trying to switch XP on is

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I am reasonably confident with code entry but it has been a long time since I did any serious UNIX work.

---

### Post by Dennis N on 2009-11-14
What VirtualBox version did you install?

Two answers I can give:
DKMS is installed with Virtual Box 3.
You can install an OS either from CD or ISO image.

Note: If you have an OEM CD (in contrast to a retail CD) from a different computer it probably will not authenticate. They are tied to the original machine they came with.

---

### Post by mikewhatever on 2009-11-15
> **truing said:**
> 

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.



There seems to be a problem with VirtualBox's kernel module. It happened to me once, after having upgraded Virtual Box to a newer version. Try running **sudo /etc/init.d/vboxdrv setup** in Terminal, enter your password and wait for it to recompile the kernel module. DKMS package should be installed by default, so no worries here.

---

### Post by truing on 2009-11-17
Thanks for your solution which worked perfectly. Now to install my programs and see how things go, it is a stand-alone piece of software for running a piece of automatic test equipment. The package refuses to work under WINE so this should be the solution and will enable me to do some experimenting with some test parameters in it's own virtual machine environment. A virtual ATE running in a virtual pc ... could be fun!

---


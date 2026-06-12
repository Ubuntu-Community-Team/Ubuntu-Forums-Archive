---
title: "problems with virtual box"
date: 2009-05-15
forum: General Help
---

### Post by banana jama on 2009-05-15
when i try to run virtual box i get the following: 
VirtualBox - Error in suplibOslnit
> Kernel driver not installed (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

i google the problem and found a solution and ran the codes suggested :
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
```

this was the out put (in short it didn't work) i didn't put the output from apt-get update because it is super long but it was successful: 
```
akeem@akeem-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
akeem@akeem-laptop:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-11-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common libmikmod2 libswfdec-0.8-0 libsdl-mixer1.2
  libsdl-image1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
akeem@akeem-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common libmikmod2 libswfdec-0.8-0 libsdl-mixer1.2
  libsdl-image1.2 libsmpeg0
The following packages will be REMOVED:
  libmikmod2 libsdl-image1.2 libsdl-mixer1.2 libsmpeg0 libswfdec-0.8-0
  nvidia-kernel-common
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 2236kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151738 files and directories currently installed.)
Removing libsdl-mixer1.2 ...
Removing libmikmod2 ...
Removing libsdl-image1.2 ...
Removing libsmpeg0 ...
Removing libswfdec-0.8-0 ...
Removing nvidia-kernel-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
akeem@akeem-laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                            
 * Cannot change owner vboxusers for device /dev/vboxdrv
akeem@akeem-laptop:~$ 

```

i don't know what else to do. also i have the DKMS package already installed.

---

### Post by Kareeser on 2009-05-15
Try this:

```
sudo chown root:vboxusers /dev/vboxdrv 
```

---

### Post by banana jama on 2009-05-15
this was the output:
> chown: invalid group: `root:vboxusers'

---

### Post by Kareeser on 2009-05-15
Hm. Have you tried reinstalling Virtualbox?

```
sudo apt-get purge virtualbox-2.2
```
(or virtualbox-ose if you are using the open source version)

Also remove the .VirtualBox folder in your home folder.

Please note that your virtual hard disks and machines are kept in that folder!

---

### Post by banana jama on 2009-05-16
thanks Kareeser it worked. one thing though does this means that i will have to uninstall and reinstall every time a new kernel is release (i read on sites that this is because of dkms and im not sure reinstalling vb solved the issue)

---

### Post by Regenweald on 2009-05-16
Have you added yourself to the vbox group ? there are instructions in the Vbox manual that guide you through creation of the group and addition of yourself if need be. I ran into similar problems myself a while back. Once you are a member of the group, setting up teh kernel driver after a kernel upgrade is simply to execute the command.

---


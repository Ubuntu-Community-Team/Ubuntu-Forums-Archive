---
title: "cannot setup virtualbox 2.0.4 in ubuntu 8.10"
date: 2008-11-14
forum: Desktop Environments
---

### Post by mozartvn on 2008-11-14
when I setup virtualbox 2.0.4 in ubuntu 8.1, I catch this error. Plz help me. Thank u very much.:KS
Here is log file of virutal 2.0.4 while I setup.
> Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.0.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.0.4/source ->
                 /usr/src/vboxdrv-2.0.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-18-generic cannot be found at
/lib/modules/2.6.24-18-generic/build or /lib/modules/2.6.24-18-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

---

### Post by binbash on 2008-11-14
you have to install kernel-devel

---

### Post by mozartvn on 2008-11-15
> **binbash said:**
> you have to install kernel-devel

hi binbash.
I found this thread : [http://ubuntuforums.org/showthread.php?t=925552]("http://ubuntuforums.org/showthread.php?t=925552")
sorry, I don't know how to install kernel-devel on ubuntu 8.10
```
sudo apt-get install kernel-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-devel
```
so, what should I do :(, thank U. :KS
I have just found that [https://launchpad.net/ubuntu/intrepid/i386/linux-kernel-devel/2.6.24-16.30]("https://launchpad.net/ubuntu/intrepid/i386/linux-kernel-devel/2.6.24-16.30")
It is safe, isn't it :|

---

### Post by binbash on 2008-11-15
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

install this if you dont want to mess with deps.

---

### Post by mozartvn on 2008-11-15
this is content of log file error, when I download & install. :(:(:(:(

```
Attempting to install using DKMS
removing old DKMS module vboxdrv version

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.0.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.0.4/source ->
/usr/src/vboxdrv-2.0.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-18-generic cannot be found at
/lib/modules/2.6.24-18-generic/build or /lib/modules/2.6.24-18-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
```

---


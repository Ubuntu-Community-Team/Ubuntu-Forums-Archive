---
title: "Virtual Box ISSUE"
date: 2008-12-23
forum: General Help
---

### Post by miked860 on 2008-12-23
I get this error when I try to reinstall:

```
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  

as root.
```

Well I run sudo /etc/init.d/vboxdrv setup and it gives me this:

```
miked860@miked860-desktop:~$ linux-headers uname -r
bash: linux-headers: command not found
miked860@miked860-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for miked860: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
miked860@miked860-desktop:~$
```

I open the log and here is what it says:

```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.0
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.0/source ->
                 /usr/src/vboxdrv-2.1.0

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.27-9-generic cannot be found at
/lib/modules/2.6.27-9-generic/build or /lib/modules/2.6.27-9-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

Someone please help me, I've had this problem for a few days now and haven't been able to find anything.

---

### Post by jerome1232 on 2008-12-23
Try installing the headers for your kernel, then running that setup program.

```
sudo apt-get install linux-headers-generic
```

---

### Post by binbash on 2008-12-23
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


did you install linux-headers?I think it is the problem

---


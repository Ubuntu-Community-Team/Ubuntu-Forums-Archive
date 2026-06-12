---
title: "access to file system denied"
date: 2009-05-28
forum: General Help
---

### Post by jdeluca5 on 2009-05-28
hello all,   I am a pretty new user to ubuntu and have a problem i cant seem to figure out. About two weeks ago, i installed virtual box, and have been using it ever since. Today, when trying to access the windows i am running on virtual box, i am confronted with the following message:   Failed to open a session for the virtual machine Windows Xp. Virtual machine 'Windows Xp' has terminated unexpectedly during startup.    The details read:   Result Code:  NS_ERROR_FAILURE (0x80004005) Component:  Machine Interface:  IMachine {13420cbb-175a-4456-85d0-301126dfdec7}    After this, another window pops up and says:   Kernel driver not installed (rc=-1908  The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing  '/etc/init.d/vboxdrv setup'  as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.    I have downloaded DKMS, ran the code they suggested in the terminal, and it seems that somehow the permission on my file system was changed.. 'root' is the owner and i now have no ability to change any files within the file system. Any help is greatly appreciated, thanks a bunch,  Jeff

---

### Post by clonne4crw on 2009-05-28
Is the user that you are running as in the vboxusers group? Make sure it is. That's what always caused me problems.

---------edit:----------
I think it's 'vboxusers'. I might be wrong. Look for something like that.

---


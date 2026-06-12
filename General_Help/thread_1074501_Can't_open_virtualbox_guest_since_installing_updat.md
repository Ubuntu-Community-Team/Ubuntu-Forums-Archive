---
title: "Can't open virtualbox guest since installing updates"
date: 2009-02-19
forum: General Help
---

### Post by Indyviews on 2009-02-19
Yes I goofed..on the umpteenth install I failed to install DKMS first. I am working on getting shared folders to work in guest windows 2000 and Ubuntu 8.10.

I decided to get the 258 updates installed and afterwards when trying to open guest Windows I get:

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

After doing this I get:

 /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 342: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
steve@steve-desktop:~$  /var/log/vbox-install.log
bash: /var/log/vbox-install.log: Permission denied
steve@steve-desktop:~$ 


I have put my password in the terminal...does anyone know what I should do now short of reinstalling Ubuntu and virtualbox and starting completely over. I say this because removing Virtualbox seems impossible. Please try to make it simply...I don't understand most of this.

---

### Post by howefield on 2009-02-19
Just to check, did you precede the command with sudo ?

ie 

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Indyviews on 2009-02-19
Thanks **Howefield**, it has  while since I sudoed and I forgot to do so. This has solved my problem of getting the guest OS back on...now to tackle the final touches on 'Shared Folders'. I appreciate your help!

---


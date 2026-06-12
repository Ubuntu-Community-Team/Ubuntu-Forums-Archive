---
title: "After installing updates w/fresh 9.04 ubuntu install, initramfs-tools wont configure"
date: 2009-06-25
forum: Desktop Environments
---

### Post by frmdstryr on 2009-06-25
Just installed ubuntu studio 9.04 on my laptop.  Works fine, I ran the update manager, and installed a few updates and now I can't install anymore programs.  

It tells me to "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
", which I tried and it responds...
```

xxxx@HP:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-3-rt
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.28-3-rt
dpkg: subprocess post-installation script returned error exit status 1

```

Should I just try to reinstall?  Thanks.

---


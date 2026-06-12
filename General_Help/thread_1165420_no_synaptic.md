---
title: "no synaptic"
date: 2009-05-20
forum: General Help
---

### Post by dsimpson on 2009-05-20
I tried to download my updates and they failed to update completely, and then I was going to download some software through synaptic and received the message: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I ran the dpkg -- configure -a it defaulted to another error message as below. How can I fix this?



eaglesoldier@eaglesoldier-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by khelben1979 on 2009-05-20
Have this worked before on the system you now are currently using?

---

### Post by bacardiandwatermelon on 2009-05-20
[http://ubuntuforums.org/showthread.php?t=1165484](http://ubuntuforums.org/showthread.php?t=1165484)
This may help...

---

### Post by dsimpson on 2009-05-21
kelbin1979,
    The answer is yes, but this is a new install, and I was dealing with boot issues, got that all resolved and now this popped up when trying to install a missing video codec that was needed to view a page. 

bacardiandwatermelon
    I tried the link and the solution listed but got the same error message when I tried to purge, and when I tried to install. I went through the steps 3 separate times to see if I had done anything wrong, a couple of times typing in the commands myself and even cutting and pasting but no go.

Any other suggestions? Thank you for your help so far.

---


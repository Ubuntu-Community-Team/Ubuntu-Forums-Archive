---
title: "[SOLVED] Problem with nvidia, restricted drivers manager and kernel modules"
date: 2008-04-10
forum: Desktop Environments
---

### Post by lapwing on 2008-04-10
Hi,

I am trying to get the nvidia-legacy driver to run. I installed the driver using apt-get, but the kernel module will not load. I tried modprobe nvidia, but it can't find the nvidia.ko modules. Secondly, I tried modprobe nvidia_legacy which gives a fatal error while installing the driver.

Finally, I tried firing up the restricted drivers manager, but that one complains that I should install linux-restricted-modules-2.6.22.1. However apt cannot install that package (it does not exist).

What has gone wrong? Am I running some unsupported kernel somehow?
I have the following kernel entries in grub:

title           Ubuntu 7.10, kernel 2.6.22.1   (edit: the one I am running currently, see reply below)
title           Ubuntu 7.10, kernel 2.6.22-14-386
title           Ubuntu 7.10, kernel 2.6.22-14-generic
title           Ubuntu 7.10, kernel 2.6.17-11-generic
title           Ubuntu 7.10, kernel 2.6.17-10-generic

Thanks in advance!

The commands and errors:
```
root@telemachus:~# modprobe nvidia
FATAL: Could not open '/lib/modules/2.6.22.1/kernel/drivers/video/nvidia.ko': No such file or directory

```

```
root@telemachus:~# modprobe nvidia_legacy
FATAL: Error running install command for nvidia_legacy

```

---

### Post by warp99 on 2008-04-10
Open a terminal and issue the following:

```
uname -r
```

Post the results to this thread.

---

### Post by lapwing on 2008-04-14
Sorry for the late reply. Here we go
```
sander@telemachus:~$ uname -r
2.6.22.1
```

---

### Post by warp99 on 2008-04-14
That kernel is not from the Ubuntu repositories so there is not going to be a package for restricted drivers to run against that kernel. We need to remove some of this cruft so we can install the correct restricted drivers packages. So first:

Boot the computer under kernel line 'Ubuntu 7.10, kernel 2.6.22-14-generic' then issue the following commands:

```
sudo apt-get remove --purge linux-image-2.6.22.1 linux-image-2.6.22-14-386 linux-image-2.6.17-10-generic 
```
this will allow you to run the current kernel and one version of the previous kernel as a backup, then issue the following:
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx-legacy
```
once that's completed issue the following:
```
sudo dpkg-reconfigure xserver-xorg
```
do not run auto-detect and choose 'nvidia' as your driver. When you get to the monitor section choose the resolution you would like from the choices given then remove the others from the list. When that is completed issue a 'sudo reboot' to reload the new drivers.

---

### Post by lapwing on 2008-04-17
This solution worked. Thanks for your help!

---


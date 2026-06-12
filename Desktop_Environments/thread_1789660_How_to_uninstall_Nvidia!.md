---
title: "How to uninstall Nvidia!?"
date: 2011-06-24
forum: Desktop Environments
---

### Post by linuxiano on 2011-06-24
Hello

*i tried to remove it from Ubuntu software center(same for other apps)
*sudo apt-get remove nvidia-glx
*sudo sh NVIDIA* --uninstall

but it's still there!!, im  using Ubuntu 10.04

---

### Post by ankspo71 on 2011-06-24
Hi,
Try uninstalling the nvidia driver by using Synaptic Package Manager instead. Open Synaptic up and search for nvidia and see which nvidia packages are still installed. Mark the correct ones for removal then click apply.

nvidia-glx-*** are now 'transitional' packages (meta packages) only used to automatically install different nvidia driver packages. For example, the package called nvidia-glx-173 is not a package with a driver inside it, but it has a set of instructions to install the driver package called "nvidia-173". Removing the nvidia-glx-*** package would probably not remove the driver it was instructed to install.
[http://packages.ubuntu.com/search?keywords=nvidia&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=nvidia&searchon=names&suite=lucid&section=all)

Hope this helps.

---

### Post by _0R10N on 2011-06-24
Did you try with 
```
aptitude purge
```
I rather use aptitude for managing packages, I've never got a problem with it.

---

### Post by linuxiano on 2011-06-25
thanks for replies..i delete it using synaptic package manger

---


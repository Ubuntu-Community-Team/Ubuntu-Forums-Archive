---
title: "Installing Nvidia Drivers"
date: 2006-03-11
forum: Desktop Environments
---

### Post by tamu70 on 2006-03-11
Being new to both Ubuntu and Linux, I need assistance in installing Nvidia drivers.  I have downloaded the latest Nforce 430 drivers and am unable to complete the installation.  Specifically, when I install the downloaded files as the root (sudo -s) in terminal, I get all the way to a screen that says the kernel source tree cannot be located.  That's where the installation stops.  Is there a simple fix or solution?  Any suggestions would be appreciated.

---

### Post by Koybe on 2006-03-11
The simple way is to get the nvidia-glx deb package. Trough synaptic or command line.
```
sudo apt-get install nvidia-glx
```

---


---
title: "Please make sure that the kernel module and all NVIDIA driver components have the sam"
date: 2011-11-08
forum: Desktop Environments
---

### Post by subehsharma on 2011-11-08
tried to manually install firefox and as i issued /.firefox i see these messages which i can't understand:


subsharm@subsharm:~/Downloads/firefox$ ./firefox
Error: API mismatch: the NVIDIA kernel module has version 280.13,
but this NVIDIA driver component has version 285.05.09.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
Error: API mismatch: the NVIDIA kernel module has version 280.13,
but this NVIDIA driver component has version 285.05.09.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.

Anyhelp would be greatly appreciated!

---

### Post by subehsharma on 2011-11-08
subsharm@subsharm:~$ dpkg-query -l | grep nvidia
ii  nvidia-current                                                 280.13-0ubuntu6                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                                                280.13-0ubuntu2                         Tool of configuring the NVIDIA graphics driver
subsharm@subsharm:~$

---

### Post by subehsharma on 2011-11-09
Migrated to Xubuntu..Sick of Ubuntu's Unity/Gnome 3.

---


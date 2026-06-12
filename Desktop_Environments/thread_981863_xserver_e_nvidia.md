---
title: "xserver e nvidia"
date: 2008-11-14
forum: Desktop Environments
---

### Post by gustavolinux on 2008-11-14
People, I have to install a nvidia driver, and it tells to exit the X server before I start the installation... How do i do it? "init 1" does not work, because the driver doesn't allow also... How can I tell my system to not start X at runlevel 3? 

Below, there is the message of the NVIDIA driver..

     NVIDIA Accelerated Graphics Driver for Linux-x86 (96.43.07)

ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING

THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Thanx dudes

---

### Post by overdrank on 2008-11-14
> **gustavolinux said:**
> People, I have to install a nvidia driver, and it tells to exit the X server before I start the installation... How do i do it? "init 1" does not work, because the driver doesn't allow also... How can I tell my system to not start X at runlevel 3? 

Below, there is the message of the NVIDIA driver..

     NVIDIA Accelerated Graphics Driver for Linux-x86 (96.43.07)

ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING

THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Thanx dudes

Hi and you can use the alt, ctrl, F1 keys to reach the virtual terminal and enter the command ```
sudo /etc/init.d/gdm stop
```

---


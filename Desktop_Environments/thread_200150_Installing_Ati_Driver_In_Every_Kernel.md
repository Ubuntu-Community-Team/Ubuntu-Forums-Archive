---
title: "Installing Ati Driver In Every Kernel"
date: 2006-06-19
forum: Desktop Environments
---

### Post by digitalkarabao on 2006-06-19
The ATI driver is installed in the default Ubuntu kernel and is working fine. I have installed a new kernel (one without the N60 errata patch). I ran fglrxinfo and I found out that the ATI drivers are not installed. My question is, do I have to install the ATI driver in every kernel? What must I do in order to get the ATI drivers recognized in the new kernel that I am using? Do I have to install the drivers anew or is there an easier way? Help guys. A step-by-step guide will surely help. :)

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=digitalkarabao]The ATI driver is installed in the default Ubuntu kernel and is working fine. I have installed a new kernel (one without the N60 errata patch). I ran fglrxinfo and I found out that the ATI drivers are not installed. My question is, do I have to install the ATI driver in every kernel? What must I do in order to get the ATI drivers recognized in the new kernel that I am using? Do I have to install the drivers anew or is there an easier way? Help guys. A step-by-step guide will surely help. :)[/QUOTE]
Type this in terminal:
> sudo apt-get install fglrx-kernel-source

---

### Post by pRedat0r on 2006-06-19
every time a kernel update installs I do this and it works just fine.

I reboot into recovery mode (not sure if this is 100% necessary, but I dont want anything locking the files im trying to remove):

sudo apt-get remove xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

reboot back into normal mode, login, run fglrxinfo and you should see everything is working fine.  I dont believe you need to install the kernel source, just the restricted modules for the new kernel version (which in my experience do not get installed by default when the kernel updates).

Hope that helps.  I guess this also depends on if you are using the fglrx drivers from the repos or the driver from ati, these instructions should work for using the repo versions.

feel free to correct anything if I am wrong, but this is what I have been doing and it seems to work for me.

Thanks.

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=pRedat0r]every time a kernel update installs I do this and it works just fine.

I reboot into recovery mode (not sure if this is 100% necessary, but I dont want anything locking the files im trying to remove):

sudo apt-get remove xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

reboot back into normal mode, login, run fglrxinfo and you should see everything is working fine.  I dont believe you need to install the kernel source, just the restricted modules for the new kernel version (which in my experience do not get installed by default when the kernel updates).

Hope that helps.  I guess this also depends on if you are using the fglrx drivers from the repos or the driver from ati, these instructions should work for using the repo versions.

feel free to correct anything if I am wrong, but this is what I have been doing and it seems to work for me.

Thanks.[/QUOTE]
Yes but he didn't state wether he was using a kernel from the repositories or a custom. My method will work in both but your will only work for a kernel from the repositories.

---

### Post by pRedat0r on 2006-06-19
good to know!

I had installed the ati drivers from ati's site once during the Flights and had no clue how to get them to work after a kernel update.  Luckily a few days later the driver was in the repo so I just removed all the debs that I installed and installed the repo version.  Thanks for the info!

---


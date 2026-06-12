---
title: "New KDE installation"
date: 2017-09-27
forum: Desktop Environments
---

### Post by r_widell on 2017-09-27
I messed up.
I tried upgrading from Kubuntu 14.04 to 16.04 and didn't see the part in the Release Notes that said that this is guaranteed to fail (it IS in there).
I was also complacent, since the 3 previous LTS upgrades on this system went without a hitch, so I only backed up the critical data and not the OS.

I've tried doing a clean install of Kubuntu 16.04, but the installer only permits mount points at / (root) and /home on a system configured for LVM.
My old system has 9 logical volumes, so that's a real problem.

I learned (through experimentation) that Ubuntu-Server doesn't have the mount point restriction on LVM drives, but I can't figure out how to get the KDE desktop installed.

Is there some transitional package that will install a reasonably complete KDE desktop (X11, display manager, etc) so I can get my system up and running again?

Is there an easier way?

Thanks,
ron

---

### Post by sudodus on 2017-09-27
I think that you can install Ubuntu Server (without selecting any extra software packages, only the basic tools), reboot and log in to the text screen. Then you can install whatever program packages you want, for example kubuntu-desktop, a meta package which should bring everything needed.

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop
```

After reboot you should log into Kubuntu. (I have tested this with several of the Ubuntu versions and flavours, but not with Kubuntu 16.04 LTS, so I am not 100% sure, but almost sure that it works).

---

### Post by r_widell on 2017-09-28
> **sudodus said:**
> I think that you can install Ubuntu Server (without selecting any extra software packages, only the basic tools), reboot and log in to the text screen. Then you can install whatever program packages you want, for example kubuntu-desktop, a meta package which should bring everything needed.


```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop
```

After reboot you should log into Kubuntu. (I have tested this with several of the Ubuntu versions and flavours, but not with Kubuntu 16.04 LTS, so I am not 100% sure, but almost sure that it works).


Thank you!
kubuntu-desktop is the magical incantation I was looking for.

For some unknown reason, it lost the internet connection during the install, so I had to install it again to get the last 57 packages. But the second invocation completed successfully, and after a reboot I was able to login to my plasma desktop.

Thanks again,
ron

---

### Post by sudodus on 2017-09-28
You are welcome :-)

If you are happy with the current solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---


---
title: "Ubuntu 10.10 only boots into tty1 after Update"
date: 2011-04-03
forum: Desktop Environments
---

### Post by hiKen on 2011-04-03
Hi guys

I have been trying to install ubuntu 10.10 decently on a sony vaio S13S9 laptop (since nvidia 310M causes some problems), following this guide: [http://ilker.de/ubuntu-10-10-on-vaio-vpc-s12-v9e]("here") , which said I had to edit the xorg.conf file, and boot with "nomodeset", and it worked perfectly.
In fact, everything worked fine until I installed updates trough the update manager. 
Now it only boots into tty1, and on the Nvidia log files it says:

*NVIDIA: Failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages.*

and if I try gnome-session, it says it cant find any screens.

I find it strange because everything was fine, and now it only boots into tty7 if I boot with "single nomodeset" in order to boot in failsafe graphics mode.

Maybe re-installing the drivers would solve the problem, but I didn't want to try without getting some feedback first!

Thank you

---

### Post by Krytarik on 2011-04-03
It seems like you installed the driver manually with the installer from Nvidia's website.

If so, I recommend removing the driver by following the included instructions (see below why), and doing a package based install instead, for example via "System -> Administration -> Additional Drivers". If you want to upgrade those to a more recent version:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
You shouldn't install the driver manually with those installer, because
- it is not a safe install, you can't remove the driver easily and safely
- you have to re-install the driver each time when the kernel gets upgraded
- the driver will not get updated automatically
- the driver is not necessarily considerably more recent
- the driver doesn't necessarily provide a considerable higher performance

Greetings.

---

### Post by hiKen on 2011-04-04
> **Krytarik said:**
> It seems like you installed the driver manually with the installer from Nvidia's website.

If so, I recommend removing the driver by following the included instructions (see below why), and doing a package based install instead, for example via "System -> Administration -> Additional Drivers". If you want to upgrade those to a more recent version:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
You shouldn't install the driver manually with those installer, because
- it is not a safe install, you can't remove the driver easily and safely
- you have to re-install the driver each time when the kernel gets upgraded
- the driver will not get updated automatically
- the driver is not necessarily considerably more recent
- the driver doesn't necessarily provide a considerable higher performance

Greetings.

I only installed with the .run file because I wanted to install the 256.53 version, since the 260 had some issues with the 310M.

However, I upgraded the ubuntu kernel to 2.6.36 and noticed that nomodeset is no longer required to boot, so maybe those issues have been solved.

Even so, I can't seem to find anywhere how to properly remove the drivers. Is 
```

sudo apt-get remove --purge nvidia*

```

enough?


Thanks

---

### Post by Krytarik on 2011-04-04
> **hiKen said:**
> 
Even so, I can't seem to find anywhere how to properly remove the drivers. Is 
```

sudo apt-get remove --purge nvidia*

```enough?

That would be a way to remove a packaged driver, and all the packages needed by "Additional Drivers" for Nvidia cards/chips, so you shouldn't do that!

For the removal of the manually installed driver, you need to follow its included instructions, like I said. Maybe the installer offers a respective option, but I really don't know, since I haven't used it since a while.

---

### Post by hiKen on 2011-04-04
I've installed the driver from the "Additional drivers" on the Administration menu but it's still the same!

---

### Post by Krytarik on 2011-04-04
> **hiKen said:**
> I've installed the driver from the "Additional drivers" on the Administration menu but it's still the same!
Please also run the previously stated commands to upgrade the driver to a more recent version.

Also, you may try the boot parameters "acpi=off" and "noapic".

---


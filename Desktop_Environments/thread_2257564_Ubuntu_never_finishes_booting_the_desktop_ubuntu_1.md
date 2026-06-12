---
title: "Ubuntu never finishes booting the desktop ubuntu 14.04"
date: 2014-12-20
forum: Desktop Environments
---

### Post by sean abbott on 2014-12-20
My laptop just stopped fulling booting the desktop.  I get a weird error message about an invalid file before the login screen.  The login screen works fine.  I then never receive any of the unity applications - no menu bar, no unity list of applications, no notifications.  I have ubuntu 14.04, with a nvidia graphic card and the proprietary drivers

Log messages that may help:
From dmesg:
init: nvidia-persistenced main process terminated with status 1

from /var/log/upstart/lightdm.log
update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf.  Sessions still open, not unmounting

(the upstart logs don't have dates...I hope that means they're per-boot transient.)

...not sure where else to look.  I suck at graphics.

(used the console to look at the logs, natch)

---

### Post by oldfred on 2014-12-20
It sounds like a nVidia driver issue.
Do you have nVidia driver installed? 
What video card/chip?

There have been several posts where users with older nVidia cards/chips have legacy driver, but an update changed them to a newer driver that does not work.

---

### Post by sean abbott on 2014-12-28
I do have it installed.  I have a geforce 9600M. I show nvidia-319, nvidia-331, nvidia-uvm, nvidia-libopencl1-331, nvidia-opencl-icd-331, nvidia-prime, and nvidida-settings installed.

---

### Post by oldfred on 2014-12-28
Part of issue may be too many drivers. 
319 & 331 and possibly prime probably create conflicts. Only one can be installed with kernel.
Not sure if you can just uninstall 319 or have to uninstall/purge everything and install most current.

How did you install. Repository, ppa or direct from nVidia(not recommended normally)?
Generally best to just install from Ubuntu's repository. Not sure though if your 9600M needs newer version than in repository, then ppa may be better choice for newest version.

       Lists installed version, in/with your kernel:
dkms status


 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Is your dual video with Intel. or Just nVidia?
If dual video you do need prime or bumblebee.
      
 Dual graphics install nVidia prime and newer nVidia driver
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

---


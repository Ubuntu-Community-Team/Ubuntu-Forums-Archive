---
title: "NVidia binary x.org drivers"
date: 2008-12-20
forum: General Help
---

### Post by lander2k2 on 2008-12-20
I have two NVidia GeForce 7600 GS video cards running multiple displays and am trying to install the correct Nvidia driver so as to run Nvidia settings and get all of the monitors to run in Ubuntu 8.10.

Each time I've installed the NVidia binary x.org driver (I've tried version 173 and 177) it causes some conflict.  Ubuntu won't boot up afterwards.  It hangs at "Checking Battery State..."  (whatever that means).

I can drop into the command line in recovery mode.

Can anyone tell my what command will allow me to uninstall this putrid driver (version 173) that is causing this?

And does anyone know of a driver that will work?

---

### Post by cariboo on 2008-12-20
I believe you video adapter needs the 177 drivers. If you type in a terminal:

```
sudo apt-get purge nvidia-glx-173
```

The above command should remove all of the 173 depenedcies, and allow you to install the 177 drivers.

Jim

---

### Post by lander2k2 on 2008-12-20
Thanks cariboo.  You saved my hide with that.

I also had to run:

```
apt-get autoremove nvidia-173-kernel-source
```

...in order to get the system to boot up again.

I've tried to install the Nvidia binary x.org driver (versions 177, 173 and 96) and they all cause the same hang-up at boot.

At least now I can recover the system, but I still have the same basic problem.

I can't install the driver and without the driver installed I can't configure the nvidia settings in order to run all of my displays.

If anyone can point me towards a driver that will work or to a possible method to debug the regular nvidia x.org drivers it would be much appreciated.

---

### Post by RJARRRPCGP on 2008-12-20
Try this:

```
sudo apt-get install linux-headers-generic dkms nvidia-glx-177 && sudo nvidia-xconfig
```

*But, FYI, READ THIS:

At the end, it will spit out an error message accusing you of having a corrupted X Org configuration file, claiming a missing driver device line, but that error message is safe to ignore, it's a bug.*

*You will get that error message, even when the X Org configuration file is valid!*

Just reboot after you see the command line appear again.

---


---
title: "Changed kernel 386-K7 Nvidia problem"
date: 2005-01-25
forum: Desktop Environments
---

### Post by neilmc on 2005-01-25
I had the nvidia drivers working fine under the 2.6.8.1-4-386 kernel. I have just installed the 2.6.8.1-4-K7 kernel and was expecting it to break the drivers.

When X wouldn't start I just changed the device from nvidia to nv to start the old 2D driver. In the XF86 log it failed on loading the nvidia kernel.

I then removed the old 386 kernel and it's headers and rebooted and grub now only has the k7 kernel.

Now if I try and install the nvidia driver apt tries to satisfy dependencies by installing the 386 kernel and headers! Even if I install the K7 headers seperately it does this.

It's all been done with apt so far. Should I just download the driver installer from nvidia and run it?

---

### Post by machiner on 2005-01-25
Sounds like something else is wrong. 

The nvidia drivers will work if you change your kernel...once installed, always installed.

THis is NOT the same for other distro's though.

You don't want the headers, you want the source....but it's going to tell you that the drivers are already installed.

---

### Post by neilmc on 2005-01-25
I do have the kernel source installed. It's odd that when reinstalling the driver using apt it insists on loading the 386 headers and kernel.

I assumed that I would have to reinstall the drivers because I had to do this with the ati drivers on a laptop when changing from the 386 to 686 kernel. That and the fact that it came up with unable to load nvidia kernel straight after installing the k7 kernel.

I'll try the installer from nvidia and see what it does.

---

### Post by neilmc on 2005-01-25
Well, that did the trick. The nvidia installer did give a warning that the system was set to load the riva module and this would conflict.

I had a look at /etc/modules and there was no sign of a riva module and there is no sign of it when I run lsmod.

Anyway, everything 3D is good now so I'm happy.

---


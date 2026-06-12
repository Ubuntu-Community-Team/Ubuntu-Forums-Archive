---
title: "Hardware Manager tab"
date: 2011-02-09
forum: Desktop Environments
---

### Post by vuurtjie on 2011-02-09
I don't have a Hardware Manager tab under System/Administration. How can I see all the devices on my computer and be able to point to the correct drivers they should use?

---

### Post by Frogs Hair on 2011-02-09
To view hardware from the GUI install sysinfo from the software center . I will appear in system tools.

---

### Post by vuurtjie on 2011-02-09
the problem with Sysinfo is that it merely displays a list of hardware items and does not give an option of updating drivers for them. besides, it does not "see" some of the elements, e.g. webcam or SD port.

---

### Post by matt_symes on 2011-02-09
Hi

There is also hardinfo in synaptic that also contains benchmarks as well as system information but it does not allow you to update drivers.

```
sudo apt-get install hardinfo
```

You can use the command line for that type of thing anyway.

EDIT: Forgot to mention device manager

```
sudo apt-get install gnome-device-manager
```

but that also does not allow you to update drivers.

Kind regards

---

### Post by Cheesehead on 2011-02-09
Vuurtije,

Welcome to Ubuntu.

Linux handles devices *differently* from Windows. Your previous Windows experience with drivers will lead you astray and cause you much needless frustration.

In Windows, hardware interface is handled by 'drivers', and it's the user's role to install and update them.

In Linux, hardware interface is handled by kernel modules, and user merely files a bug report if the hardware interface has a problem.

See the difference? You, the user, update drivers in Windows. You update the kernel in Linux...which is just another package handled by Update Manager in Ubuntu.

Now, you probably wouldn't ask about 'drivers' if your hardware was working perfectly. What is the *real* problem you are having? The one you think can be fixed with 'drivers'?

---

### Post by matt_symes on 2011-02-09
Hi

> **Cheesehead said:**
> Vuurtije,

Welcome to Ubuntu.

Linux handles devices *differently* from Windows. Your previous Windows experience with drivers will lead you astray and cause you much needless frustration.

In Windows, hardware interface is handled by 'drivers', and it's the user's role to install and update them.

In Linux, hardware interface is handled by kernel modules, and user merely files a bug report if the hardware interface has a problem.

See the difference? You, the user, update drivers in Windows. You update the kernel in Linux...which is just another package handled by Update Manager in Ubuntu.

Now, you probably wouldn't ask about 'drivers' if your hardware was working perfectly. What is the *real* problem you are having? The one you think can be fixed with 'drivers'?

Very, very well put. =D> What is the real problem ?

Kind regards

---


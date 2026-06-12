---
title: "How to unload driver?"
date: 2009-07-31
forum: Desktop Environments
---

### Post by iamgoose on 2009-07-31
I'm trying to find out how to unload a driver called pl2303. I'm running VMware Workstation 6.5 on Ubuntu 9.0.4. Win XP is the guest OS. I have a usb-to-serial cable for connecting a device in the guest OS. Both Ubuntu and XP recognize the cable (as a "prolific USB" cable) and it is connected in the VM, but Ubuntu shows a dialog saying the device won't work because driver pl2303 in Ubuntu has a claim on the device, and to unload the driver. How?

My interpretation of this is that even though the usb-to-serial cable is recognized by XP, it can't connect to the actual peripheral device for which the cable is needed until I get Ubuntu not to recognize the device - by unloading its driver.

Thanks in advance!

---

### Post by bryonak on 2009-07-31
There's no GUI for managing kernel modules AFAICT... so let's fire up a terminal and type```
lsmod
```to see all loaded kernel modules (what you call "drivers").
You can filter the list by "piping" it into a grep:```
lsmod | grep FILTER
```
In your case, you might use "pl2303" or "pl" or "2303" as FILTER.

If the module is loaded, use modprobe (the kernel module probe) to remove (-r) it:```
sudo modprobe -r pl2303
```

To load the module again, simply type```
sudo modprobe pl2303
```

---

### Post by cariboo on 2009-07-31
To remove the driver, open an Applications-->Accessories-->Terminal and type:

```
sudo rmmod pl2303
```

To prevent the module from loading at it to the bottom of /etc/modprobe.d/blacklist, it may be blacklist.conf, I'm not on a system running Ubuntu at the moment. To add the module to the blacklist file, press Alt F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

or

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

---

